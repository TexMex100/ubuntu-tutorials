`nano /etc/nginx/sites-available/domain.conf`  
For example sharkybot.xyz  
`nano /etc/nginx/sites-available/sharkybot.conf` (not needed but better to organise)  
For example dev.sharkybot.xyz  
`nano /etc/nginx/sites-available/dev.sharkybot.conf`  


Paste this into the file (CTRL SHIFT V)
server {
  server_name <domain>;
  location / {
    proxy_pass http://191.96.52.56:<port>;
    proxy_buffering off;
    proxy_set_header X-Real-IP $remote_addr;
  }
}

proxypass ip:port must be EXACT to the servers IP address
for example:
panel.solonodes.xyz:1024
http://panel.solonodes.xyz:1024/

ln -s /etc/nginx/sites-available/FILENAME.conf /etc/nginx/sites-enabled/FILENAME.conf
you must type the full thing, you cannot use any shortcuts

systemctl restart nginx

To do the rest of the steps, they MUST have created an A record on cloudflare to the node IP.
certbot
Type the number that shows the domain you put in the files above.

If it asks to pick Redirect or No Redirect, pick Redirect

done!
