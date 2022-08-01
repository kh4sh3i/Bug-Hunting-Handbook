# Dependency Confusion

we find init file, then find private repository. after than we create this package with greatest number in public repository. and boooom!

```
- Public Registry
    - https://www.npmjs.com/
    - https://pypi.org/
    - https://rubygems.org/
- NPM installer
- versioning: Major.Minor.Patch
    - 1.0.0 -> 1.1.1
    - https://medium.com/fiverr-engineering/major-minor-patch-a5298e2e1798
- Private Registry
    - https://github.com/verdaccio/verdaccio
    - python -m pip install --index-url=http://localhost internal-a
```

### Automation

```
    - Inputs/Context -> Package Manager File 
        - github 
        - fuzzing: nuclei 
        - subfinder -d sharif.edu -silent | httpx -silent | 
        nuclei -t nuclei-templates/exposures/configs/package-json.yaml -silent | awk '{print $6}'
    - Fuzzer -> - https://github.com/visma-prodsec/confused
```

### search in github

```
- Inputs/Context -> https://sourcegraph.com + github 
https://sourcegraph.com/search?q=context:global+repo:iran-nodejs-community/digiNode.*+verify%28&patternType=literal
https://github.com/eth0izzle/shhgit
```

### find vuln package

```
https://github.com/visma-prodsec/confused
```

### find init file (DC + LFI/SSRF)

if target company not use github, then we find "LFI" bug in site and then read some file like: package.json , require.txt ,... to find private repository.

good tools for find hidden parameter in blank page for login page is arjun tools

```
- Hidden Parameter Discovery:
    - https://github.com/s0md3v/Arjun/
    - https://github.com/sh1yo/x8
```

### prevention

```
    - https://blog.packagist.com/preventing-dependency-hijacking/
```

