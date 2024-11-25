Alright last stretch.

* $ sudo zammad run rails r "Setting.set('es_url', 'http://localhost:9200')"
* $ zammad run rails r "Setting.set('es_user', 'elastic')"
* $ zammad run rails r "Setting.set('es_password', 'changeme')"

The default elasticsearch password is by default "changeme"

![image](https://github.com/user-attachments/assets/75b307cd-c379-4714-aa8c-c01b7acbbba6)

One last step is to change the default port for nginx. After following all these steps you should have been able to login the default nginx page
Now let's login:

![image](https://github.com/user-attachments/assets/688ff755-2919-44dc-b64d-66198e3ae584)

let's change the port from 80 to 81

 nano /etc/nginx/sites-available/zammad.conf

 let's cange the server listen port to 81
 server {
  listen 81;
  listen [::]:81;
  
![image](https://github.com/user-attachments/assets/829966a7-c932-43bc-a546-091962a02991)

![image](https://github.com/user-attachments/assets/5d0792f9-7ac3-4a18-84c0-c3a10b0e0d5e)
