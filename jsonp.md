---
description: >-
  JSONP, or JSON-P (JSON with Padding), is a historical JavaScript technique for
  requesting data by loading a <script> element
---

# JSONP

JSONP stands for **JSON with Padding**. Requesting a file from another domain can cause problems, due to cross-domain policy. Requesting an external script from another domain does not have this problem. JSONP uses this advantage, and request files using the script tag instead of the XMLHttpRequest object.

### example

{% embed url="https://demo.sjoerdlangkemper.nl/jsonp.php" %}

```
<script src="/api/user/1"></script>
for bypass sop we can use jsonp but this function is not safe
we send json data with header : application/javascript
we use callback function that should predefine in sender
automation tools is not good. because developer use different names for callback function
```

### automation

```
    - CORS + postMessage + JSONP
    - JSONP: https://github.com/kapytein/jsonp
```

