# External Recon

### 1) public Datasets (internet wide scanning)

```
       1.project censys  -> IPv4 -> services -> REST API 
            ZMAp (scanner) ->  ZGrab (banner grabbing) -> Dataset 
         
       2.Project Sonar
	    https://opendata.rapid7.com/
            - project crobat: Searchable Open Source DNS Database
	    https://sonar.omnisint.io/
```

```
crobat -s uber.com > uber_result
```

### 2) CT search engines

```
        https://crt.sh/?q=%25.tesla.%25
        https://sslmate.com/certspotter/
```

### DNS aggregators

Passive DNS Scanning: virustotal, dnsdumpster

### search engine

google hacking

### wrappers

subfinder: Public Engines (censys) + sublist3r + brute-forcing

```
https://github.com/projectdiscovery/subfinder
```

### wayback machine

```
gau (getAllUrls)
https://github.com/lc/gau
gau -subs uber.com | cut -d / -f3 | sort -u > gau_result 
```

### subdomain brute-forcing

```
    - index 
    - internal usages -> dev stage 
        wordlist -> test, abcdef 
        [a-zA-Z].taret.com (subbrute) -> domains -> DNS Resolver -> online services 
            t1.sub.target.com 
            t2.sub.target.com
            .... 
    massdns + subbrute 
    https://github.com/blechschmidt/massdns
https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056/raw/96f4e51d96b2203f19f6381c8c545b278eaa0837/all.txt
```

```
./scripts/subbrute.py lists/names.txt uber.com | ./bin/massdns -r lists/resolvers.txt -t A -o S -w massout_brute
 cat massout_brute | awk '{print $1}' | sed 's/.$//' | sort -u
```

### Subdomain Permutaions

```
uber.com 
    store.uber.com 
    delivery.uber.com 
test, stage -> production 

    store-test.uber.com 
    delivery-stage.uber.com 
    api.uber.com 
    api-dev.uber.com 
   ---------------------------
   target.com 
        a.target.com 
        stage.a.target.com 
        a.stage.target.com 
        a-stage.target.com
        a-dev.target.com
```

```
altdns -> words + domains 
https://github.com/ProjectAnte/dnsgen

dnsgen -> DNS Resolver (massdns) 
cat testdomains | dnsgen - | ./bin/massdns -r lists/resolvers.txt -t A -o S -w massout_dnsgen
```

### Horizontal Enumeration vs vertical Enumeration

```
Horizontal 
        target.com 
        a.target.com 
        b.target.com 
vertical
        test-target.com
        a.dev-target.com
        ubertest.com
```

```
vertical discovery subdomains with amass...
amass enum -d $domain -ip -src

horizantal discovery subdomains with amass...
amass intel -d $domain -whois

get new subdomains with amass track...
amass track -d $domain
```
