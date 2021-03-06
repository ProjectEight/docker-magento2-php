# Description

This image is built from the official [`php`](https://hub.docker.com/_/php/) repository and contains PHP configurations for Magento 2.

# What's in this image?

This image installs the following base packages:

- `composer`
- `php-fpm`

This image also installs the following PHP extensions, which are the minimally required extensions to install and run Magento 2:

- `bcmath`
- `gd`
- `intl`
- `mbstring`
- `mcrypt`
- `pdo_mysql`
- `soap`
- `xsl`
- `zip`

## Variables

The following variables may be set to control the PHP environment:

- `PHP_MEMORY_LIMIT`: (default `16G`) Set the memory_limit of php.ini
- `PHP_PORT`: (default: `9000`) Set a custom PHP port
- `PHP_PM`: (default `dynamic`) Set the process manager
- `PHP_PM_MAX_CHILDREN`: (default: `20`) Set the max number of children processes
- `PHP_PM_START_SERVERS`: (default: `8`) Set the default number of servers to start at runtime
- `PHP_PM_MIN_SPARE_SERVERS`: (default `4`) Set the minumum number of spare servers
- `PHP_PM_MAX_SPARE_SERVERS`: (default: `12`) Set the maximum number of spare servers
- `APP_MAGE_MODE`: (default: `developer`) Set the MAGE_MODE

## Building it

Run the `build` command to build the image:

```bash
$ docker build -f dist/7.0-fpm/Dockerfile -t projecteight/php7.0-fpm:0.3.0 -t projecteight/php7.0-fpm:latest ./dist/7.0-fpm/
$ docker images
REPOSITORY                   TAG                 IMAGE ID            CREATED             SIZE
projecteight/php7.0-fpm      0.3.0               166bdd0cbc92        About an hour ago   183 MB
projecteight/php7.0-fpm      latest              166bdd0cbc92        About an hour ago   183 MB
...
```

## Using it

This image is intended to be used with the [docker-magento2-compose](https://github.com/projecteight/docker-magento2-compose)  project

## One-off containers

This image can run one-off PHP commands, such as:

`docker run --rm --name php-test projecteight/magento2-php echo "Hello world"`

Application code is placed in `/var/www/html`. You can also attach a volume to that location, then run Magento-specific commands such as the Magento CLI tool:

`docker run --rm --name mysite -v /Users/username/Sites/mysite/app/code:/var/www/html/app/code projecteight/magento2-php:{PHPVERSION}-fpm-0 ./bin/magento`
