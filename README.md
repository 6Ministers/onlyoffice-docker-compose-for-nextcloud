# Installing OnlyOffice with docker-compose.

## Quick Installation

**Before starting the instance, direct the domain (subdomain) to the ip of the server where NextCloud will be installed!**

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

Download nextcloud instance:


``` bash
curl -s https://raw.githubusercontent.com/6Ministers/onlyoffice-for-nextcloude/master/download.sh | sudo bash -s nextcloud
```

If `curl` is not found, install it:

``` bash
$ sudo apt-get install curl
# or
$ sudo yum install curl
```

Go to the catalog

``` bash
cd nextcloud
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

Then open `https://nextcloude.domain.com:` to access OnlyOffice

On this page, you will need to specify the settings for your installation.


## OnlyOffice container management

**Run nextcloude**:

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
