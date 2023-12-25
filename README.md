# Installing OnlyOffice with docker-compose.

## Quick Installation

**Before starting the instance, direct the domain (subdomain) to the ip of the server where OnlyOffice will be installed!**

## 1. OnlyOffice Server Requirements
From and more
- 2 CPUs
- 2 RAM 
- 10 Gb 

Run for Ubuntu 22.04

``` bash
sudo apt-get purge needrestart
```

Install docker and docker-compose:

``` bash
curl -s https://raw.githubusercontent.com/6Ministers/onlyoffice-for-nextcloude/master/setup.sh | sudo bash -s
```

Download onlyoffice instance:


``` bash
curl -s https://raw.githubusercontent.com/6Ministers/onlyoffice-for-nextcloude/master/download.sh | sudo bash -s onlyoffice
```

If `curl` is not found, install it:

``` bash
$ sudo apt-get install curl
# or
$ sudo yum install curl
```

Go to the catalog

``` bash
cd onlyoffice
```

To change the domain in the `Caddyfile` to your own

``` bash
https://subdomain.your-domain:443 {
    header Strict-Transport-Security max-age=31536000;
    reverse_proxy localhost:2291
	encode zstd gzip

...	
}
```

**Run onlyoffice:**

``` bash
docker-compose up -d
```

Then open `https://onlyofice.domain.com:` to access OnlyOffice

On this page, you will need to specify the settings for your installation.

A random secret is generated automatically if a custom secret has not been added during installation. To obtain the default secret, run this command:
``` bash
 sudo docker exec 728397ce5f45 /var/www/onlyoffice/documentserver/npm/json -f /etc/onlyoffice/documentserver/local.json 'services.CoAuthoring.secret.session.string'
```

![Screenshot_77896](https://github.com/6Ministers/onlyoffice-for-nextcloude/assets/11208423/d49c08a1-8f21-43ce-badb-4fa75390b570)


Connect your Only Office to Nextcloud

![Screenshot_76](https://github.com/6Ministers/onlyoffice-for-nextcloude/assets/11208423/89471cac-c7b8-4a9d-9bad-6e0e9162b823)

## OnlyOffice container management

**Run onlyoffice**:

``` bash
docker-compose up -d
```

**Restart**:

``` bash
docker-compose restart
```

**Restart**:

``` bash
sudo docker-compose down && sudo docker-compose up -d
```

**Stop**:

``` bash
docker-compose down
```

## Documentation

