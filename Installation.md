### On new VPS
Copy installtion scripts into root folder
```
Run install.sh
```
Install Elasticsearch and Tesseract OCR see documentation <br>
https://najigram.com/2022/02/setup-elasticsearch-7-for-nextcloud/ <br>
https://markus-blog.de/index.php/2018/06/21/how-to-install-fulltextsearch-in-nextcloud-13-with-elasticsearch-and-tesseract-ocr/

### Install Evolvecloud
```
Run install_nc.sh
```
### Visit instance url (Do not sign up)

Add following code in /var/www/ec_instance/config/config.php 
```
'default_phone_region' => 'SG', 'skeletondirectory' => ''
```
and signup.

Add elasticsearch indexes 

Add cronjobs


