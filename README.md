# tranliterator
en -> ru+en transliterator app
config.py contains the TRANSLATOR_ID and TRANSLATOR_SECRET variables
of the microsoft translator client_id and client_secret keys

https://datamarket.azure.com/dataset/bing/microsofttranslator#terms
register the microsoft account, then in this page click MY ACCOUNT,
then DEVELOPERS button in the left column and click REGISTER button
you will register the application. The application client_id and
client_secret will the the TRANSLATOR_ID and TRANSLATOR_SECRET
variables.

## Development

```bash
git clone https://github.com/rebyatishki/tranliterator
cd transliterator
pip install -r requirements.txt
cp contrib/config-example.py config.py
# edit config.py
export APP_SETTINGS="config.DevelopmentConfig"
python run.py
```

## Installation in production

```bash
sudo su -
mkdir -p /var/www/transliterator
git clone https://github.com/rebyatishki/tranliterator /var/www/transliterator
cd /var/www/transliterator
pip install -r requirements.txt
apt-get install -y nginx uwsgi uwsgi-plugin-python
cp contrib/config-example.py config.py
# edit config.py
cp contrib/uwsgi.ini /etc/uwsgi/apps-available/transliterator.ini
ln -s /etc/uwsgi/apps-available/transliterator.ini /etc/uwsgi/apps-enabled/transliterator.ini
service uwsgi restart
cp contrib/nginx.conf /etc/nginx/sites-enabled/transliterator.conf
# edit /etc/nginx/sites-enabled/transliterator.conf
service nginx restart
```
