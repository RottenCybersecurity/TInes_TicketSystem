# Tines_TicketSystem
This is a continuation
here we will be adding our wazuh alerts and using Tines as a middle man to direct the traffic to create alerts in our fav ticketing system
this works for zendesk as tested in a production environment however here we'll be using an open source ticketing system that supports API
Zammad.

**Step 1: Setup**
We'll need a few prerequisite that i'll walk you through outherwise setup should be simple.
elasticsearch, according to the doc it isn't a hard dependency but why take chances
Installtion Elastic Search

https://docs.zammad.org/en/latest/install/elasticsearch.html

$ apt install apt-transport-https sudo wget curl gnupg
$ echo "deb [signed-by=/etc/apt/trusted.gpg.d/elasticsearch.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main"| \
  tee -a /etc/apt/sources.list.d/elastic-7.x.list > /dev/null
$ curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | \
  gpg --dearmor | tee /etc/apt/trusted.gpg.d/elasticsearch.gpg> /dev/null
$ apt update
$ apt install elasticsearch
$ /usr/share/elasticsearch/bin/elasticsearch-plugin install ingest-attachment
After you installed Elasticsearch and its attachment plugin, ensure to enable it by default and start it.

**Step 2: Configuration**

Install ingest-plugin (only for Elasticsearch <= 7)
$ sudo /usr/share/elasticsearch/bin/elasticsearch-plugin install ingest-attachment

Increase virtual memory map limit
$ sudo sysctl -w vm.max_map_count=262144

Adjust /etc/elasticsearch/elasticsearch.yml
We use the following settings to optimize the performance of our Elasticsearch servers. You may want to append that to your elasticsearch.yml as a useful basic configuration.

Nano /etc/elasticsearch/elasticsearch.yml and add http.max_content_length: 400mb on the last line. example below:

#
#  
http.max_content_length: 400mb
indices.query.bool.max_clause_count: 2000
 
Enable and start Elasticsearch
$ systemctl start elasticsearch
$ systemctl enable elasticsearch
