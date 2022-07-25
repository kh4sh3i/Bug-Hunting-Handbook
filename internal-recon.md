# Internal Recon

### Services

```
    HTTP/HTTPS 
    cat domains.txt | httprobe 
    grouping 
        10k -> 10*1k 
        sniper -> modes 
        split -l 100 uber_valid
    port scanning 
        -b -> 924 -> Docker Image 
        -t -> 2s -> 4s 
        domains -> rustscan 
        rustscan -a domains.txt --top 
```

```
    for sub in $(cat uber_file); do rustscan -a $sub --top | awk '{print $1 ":" $2}' | grep -E '(^[0-9])' > ${sub}.txt ; done
```

### Vulnerabilities

```
https://github.com/projectdiscovery/nuclei
    templates 
        1.pre-defined 
        2.custom    
    nuclei -l domains.txt -t vulnerabilities/wordpress 
Subdomain Takeover
```

```
nuclei -l domains.txt -t vulnerabilities/wordpress 
```

### content discovery

```
https://github.com/ffuf/ffuf
https://github.com/danielmiessler/SecLists
ffuf -u http://pour-feliciter.cz/FUZZ -w directories.dat -mc 200 -o ffuf_result 
cat ffuf_result | jq -r .results[].url         
https://github.com/epi052/feroxbuster
    200 results -> 200.txt 
        403,401 -> 401-403.txt -> Dirdar 
    https://github.com/M4DM0e/DirDar
```

### sensitive file

```
subdomains -> EXTs -> db, log, zip 
echo rouhani.ir | waybackurls | deduplicate --hide-images -sort | grep -iE '(\.(sql|bak|log))' 
gau -subs target.com | deduplicate --hide-images --sort | httpx -silent | grep -iE '(\.(sql|bak|log))' | tee -a sensitive_files 
```

### Grouping

```
404,403,401
	cat resolved_domains| httpx -status-code
	cat resolved_domains | httpx -status-code -mc 404,403,401 -silent | awk '{print $1}' | feroxbuster --stdin -no-resucrsion
	cat sony | dnsx | httpx -status-code -mc 404,403,401 | awk '{print $1}' 
```

```
200 :
	1. blank 
	- Directory + Files Fuzzing 
	- wayback 
	- Content Discovery (Burp Suite)
	- Google Dork 
	- Parameters 
	- Public -> Paramspider 
		python3 paramspider.py -d https://talumm.org/ -e js,css,ttf,woff,svg
	- Hidden -> Arjun 
	- JS endpoints 
	2. Single Login Page  
	3. CMS-Based 
	4. Auth + other functions 
```

### screenshot

use eyeWitness tools

