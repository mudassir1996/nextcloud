### On new server
Copy installtion scripts into root folder
```
bash install_server.sh
```
Install Elasticsearch and Tesseract OCR see documentation <br>
https://najigram.com/2022/02/setup-elasticsearch-7-for-nextcloud/ <br>
https://markus-blog.de/index.php/2018/06/21/how-to-install-fulltextsearch-in-nextcloud-13-with-elasticsearch-and-tesseract-ocr/

### Install Evolvecloud
```
bash install_ec_instance.sh
```
### Install clamav
### Visit instance url (Do not sign up)

Add following code in /var/www/ec_instance/config/config.php 
```
'default_phone_region' => 'SG', 
  'skeletondirectory' => '',
  'memcache.local' => '\\OC\\Memcache\\APCu',
  'distributed' => '\\OC\\Memcache\\Redis',
  'memcache.locking' => '\\OC\\Memcache\\Redis',
  'filelocking.enabled' => 'true',
  'redis' => 
  array (
    'host' => '/var/run/redis/redis-server.sock',
    'port' => 0,
    'timeout' => 0.0,
  ),
  'preview_libreoffice_path' => '/usr/bin/libreoffice',
  'integrity.check.disabled' => true,
  'trashbin_retention_obligation' => '365, auto',
  'knowledgebaseenabled' => false,
```
and signup.

Add elasticsearch indexes 

Add Backup file at /var/www
```
backup.sh
```
Add cronjobs

### SSL installation (if needed)
```
certbot --apache
```

### Add HTTP header
```
<IfModule mod_headers.c>
  Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
</IfModule>
```


