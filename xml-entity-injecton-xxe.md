# IDOR

### Objects

```
Data/Object -> User 
- profile 
- post 
- photo 
- comment 
- document 
```

### Methodology

```
1) Objects 
2) ObjectIDs 
3) Exploit 
    ObjectIDs 
        1) Int 
        2) encoded 
        3) encrypted  
            GUID, UUID 
```

```
- objects 
    - post 
    - comment -> IDOR 
    - add video 
    - add page 
    - add group 
    - settings 
        - basic info 
        - email 
        CSRF + Self-XSS 
        IDOR + Self-XSS 
        IDOR -> SQLI 
```

### automation

```
 Authorize + Autorepeater 
```
