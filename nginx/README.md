# Config Nginx
	sudo apt-get install nginx

## Config Files
 - sudo nano /etc/nginx/sites-available/SITE_NAME
---
	sudo ln -s /etc/nginx/sites-available/SITE_NAME /etc/nginx/sites-enabled
	sudo nginx -t
	sudo systemctl restart nginx
	sudo ufw delete allow 8080
	sudo ufw allow 'Nginx Full'
	sudo systemctl enable nginx