# Django

**Run these commands as none root user**

	sudo apt-get update
	sudo apt-get install python3-pip
	sudo -H pip3 install --upgrade pip
	sudo -H pip3 install virtualenv virtualenvwrapper
	echo "export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3" >> ~/.bashrc
	echo "export WORKON_HOME=~/Env" >> ~/.bashrc
	echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bashrc
	source ~/.bashrc
---
	mkvirtualenv mysite
	pip install django
---

### Update in `settings.py`:
- ALLOWED_HOSTS
- STATIC_URL = '/static/'
- STATIC_ROOT = os.path.join(BASE_DIR, 'static/')
---
	~/mysite/manage.py collectstatic
	sudo ufw allow 8080

## Deploy using uwsgi emperor mode

**Install uwsgi system-wide:**

	sudo pip install uwsgi

**Create and test `uwsgi.ini`:**
	
	uwsgi --ini uwsgi.ini

**Put `uwsgi.ini` file in emperor directory:**
	
	mv uwsgi.ini /home/mmd/uwsgi
	
**Create `uwsgi.service`:**
		
	sudo vim /etc/systemd/system/uwsgi.service
	
**Test it:**

	sudo systemctl daemon-reload
	sudo systemctl restart uwsgi

**Install nginx**

	sudo apt-get install nginx

**Create `nginx` config file:**

	sudo vim /etc/nginx/sites-available/mysite

**Put it in site-available:**

	sudo ln -s /etc/nginx/sites-available/mysite /etc/nginx/sites-available/mysite

**Test nginx**

	sudo nginx -t
	
**Restart everything**

	sudo systemctl restart nginx
	sudo systemctl start uwsgi
	sudo ufw allow 'Nginx Full'
	sudo systemctl enable nginx
	sudo systemctl enable uwsgi

### Some help:

* Nginx error log:	

		sudo tail -F /var/log/nginx/error.log
		
* Check `.sock` file permissions to top:

		namei -nom /run/uwsgi/mysite.sock
	```
	f: /run/uwsgi/mysite.sock
	 drwxr-xr-x root  root     /
	 drwxr-xr-x root  root     run
	 drwxr-xr-x mmd www-data uwsgi
	 srw-rw---- mmd www-data mysite.sock
	```
* Some notes on deploying another site:
	* Copy files
	* Change permissions to your user
	* Change `.sock` permissions to 660
	* Restart `uwsgi` after adding new `.ini` file
	* Make sure virtualenv is not in a root directory ;)



### Refs: [Digitalocean](https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-uwsgi-and-nginx-on-ubuntu-16-04), [A Gist page](https://gist.github.com/evildmp/3094281), [Stackoverflow](https://stackoverflow.com/a/40041214/6455331)