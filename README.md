## Introduction

A dumping ground for a variety of Nginx configurations which have used in one or another.

## Ubuntu utilities

Some may come already installed but if not, this should cover it. Please note this for Ubuntu 16.04.

```
sudo apt-get install -y curl git letsencrypt mailutils software-properties-common wget zip unzip
```

## Useful Commands

```
sudo nginx -t
```

## Let's Encrypt

Based on the parts/letsencrypt.conf, the following command should be used to get the SSL certificate. This is based on the /srv/letsencrypt/ folder already exists.

Note; CertBot will automatically create the ".well-known/" folder.

```
sudo letsencrypt certonly --webroot -w /srv/letsencrypt/ -d DOMAIN
```

## WordPress CLI - Fresh Installation

Ensure that the word "wordpress" is replaced by the actual name of your website. Especially useful if you wish to install multiple websites.

### Created folder

```
mkdir /srv/wordpress/
cd /srv/wordpress/
```

### Install WordPress

```
wp core download --locale=en_GB
wp core config --prompt
wp core install --prompt
wp plugin install advanced-custom-fields jetpack redirection redis-cache regenerate-thumbnails rewrite-rules-inspector wordfence wordpress-seo wp-crontrol
wp core language update

sudo chown www-data:www-data -R wp-content/uploads
```

### Configure WordPress

```
wp media regenerate
wp redis enable
wp user update joe@email.com --user_pass=
```
