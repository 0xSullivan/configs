# Config Django & VENV

	sudo apt-get update
	sudo apt-get install python3-pip
	sudo -H pip3 install --upgrade pip
	sudo -H pip3 install virtualenv virtualenvwrapper
	echo "export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3" >> ~/.bashrc
	echo "export WORKON_HOME=~/Env" >> ~/.bashrc
	echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bashrc
	source ~/.bashrc
---
	mkvirtualenv firstsite
	pip install django
---

### Update in settings.py:
- ALLOWED_HOSTS
- STATIC_URL = '/static/'
- STATIC_ROOT = os.path.join(BASE_DIR, 'static/')
---
	~/firstsite/manage.py collectstatic
	sudo ufw allow 8080
