Installing Zammad

We first will install the required tools:

$ sudo apt install curl apt-transport-https gnupg

This is assuming we've installed Elasticsearch, it isn't a hard dependency so we can skip it but if you run into an issue, please install.

https://github.com/RottenCybersecurity/Tines_TicketSystem/blob/main/Elasticsearch_install.md

We'll also have to ensure the correct locale to allowed Zammad to work correctly

$ locale | grep "LANG="

If above does not return <lang_code>.utf8 you can correct this issue as follows.

* $ sudo apt install locales
* $ sudo locale-gen en_US.UTF-8
* $ echo "LANG=en_US.UTF-8" > sudo /etc/default/locale

we'll now add a repository and install zammad

* $ echo "deb [signed-by=/etc/apt/keyrings/pkgr-zammad.gpg] 
 https://dl.packager.io/srv/deb/zammad/zammad/stable/ubuntu 24.04 main"| \
    sudo tee /etc/apt/sources.list.d/zammad.list > /dev/null

  * $ sudo apt update && sudo apt install zammad -y

![image](https://github.com/user-attachments/assets/0569daf6-e20a-48e9-9fae-9d36d988377c)

Let's ensure to open ports 80 and 443 by enabling ufw. This will cover only your distribution firewall so keep that in mind. 

* $ ufw allow 80 && ufw allow 443 && ufw reload

![image](https://github.com/user-attachments/assets/b3bf9d2b-b758-4565-aa20-fc22d0f12ce7)

Now that we've finished installing, let's check the status:

![image](https://github.com/user-attachments/assets/1d9b13a7-acd8-4bb0-b377-cb2ccd57cb4e)

Looks good! Good job!
