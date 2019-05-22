# Mocker - Magento 2 docker 

## Introduction

Version 1.02. of Mocker

## Preparation  

Edit `build\custom.conf`

1. Check `build\custom.conf` or leave it default 

## Building and installing

1. Run `./bin/build` and follow script instructions. 


This may take a while. Especially if You are running docker for the first time. 

## Scripts

Each build is prepared for one project. After installation You will need at least.   
After installation go to `src` folder and treat it as a default folder to invoke any action. 

* ```./docker-compose.yml``` 
* `./bin` folder.

There's helper script - `./bin/exec`. It will help you with executing commands inside of container.

Usage:
```
./bin/exec <container_suffix> <optional_command>
```
Eg.

```
bin/exec node "php -v"
```
type 
```./bin/exec -h``` for help
 

Container suffixes are: php, nginx, db.
If you don't pass an <optional_command>, then it will call `/bin/bash` by default and you'll end up inside of the container as www-data user.
If you pass an <optional_command>, it will be run as (docker) root user. 
It's more secure to not run some commands as root user. 
During building process program will copy `.build/php_bashrc` to `./php`. This file contains aliases. You can use them only inside php container. 
``` bin/exec php ```. 

For Magento 2 special commands please see / edit `bin/m2`. Example `bin/m2 -s` will invoke `bin/magento setup:static-content:deploy -f -j 4 pl_PL en_US`

By deafult Mailhog is running at port 18035.   

There is no need to keep all containers running. Eg. after system restart dockers will stop. To restart them enter:

``` bin/start.sh``` 

