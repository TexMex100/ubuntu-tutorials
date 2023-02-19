```bash
nano /etc/nginx/sites-available/domain.conf
```  
For example **texmex100.tk** (not needed but better to organise)  
```bash
nano /etc/nginx/sites-available/texmex100.conf
```
For example **dev.texmex100.tk**  
```bash
nano /etc/nginx/sites-available/www.texmex100.conf
```  

Paste this text in the file you created
```bash
server {
  server_name <domain>;
  location / {
    proxy_pass http://<ip>:<port>;
    proxy_buffering off;
    proxy_set_header X-Real-IP $remote_addr;
  }
}
```

proxypass ip:port must be EXACT to the servers IP address  
for example:  
test.texmex100.tk:1024  
>http://test.texmex100.tk:1024/

```bash
ln -s /etc/nginx/sites-available/FILENAME.conf /etc/nginx/sites-enabled/FILENAME.conf
```
you must type the full thing, you cannot use any shortcuts

```bash
systemctl restart nginx
```

**To do the rest of the steps, they MUST have created an A record on cloudflare to the node IP.**
```bash
certbot
```
Type the number that shows the domain you put in the files above.

If it asks to pick `Redirect` or `No Redirect`, pick `Redirect`

done!
