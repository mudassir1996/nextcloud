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
### Visit instance url (Do not sign up)

Add following code in /var/www/ec_instance/config/config.php 
```
'default_phone_region' => 'SG', 'skeletondirectory' => ''
```
and signup.

Add elasticsearch indexes 

Add Backup file at /var/www
```
backup.sh
```
Add cronjobs

### SSL installation (if needed)
https://che-adrian.medium.com/make-your-nextcloud-ready-for-accessing-over-the-internet-9a17116a44ce


