# Image php74 for run test

Dockerfile for create image on php7.4 for run test

# Build base image

## php 7.4.33

1. Build from root directory
```shell
docker build -f Dockerfile.base -t i3bepb/php74-for-test:0.2.0-php-7.4.33-cli-alpine3.16 .
```
2. Заливаем образ в репозитории
```shell
docker push i3bepb/php74-for-test:0.2.0-php-7.4.33-cli-alpine3.16
```
3. Так можно запустить из корня проекта, проверить
```shell
docker run --rm -it i3bepb/php74-for-test:0.2.0-php-7.4.33-cli-alpine3.16 sh
```

# How use

Build local image with local user
```shell
docker build -f Dockerfile.dev -t php74-for-test:1.0.0 --build-arg MYAPP_IMAGE=i3bepb/php74-for-test:0.2.0-php-7.4.33-cli-alpine3.16 --build-arg LOCAL_USER_ID_ARG=1000 --build-arg LOCAL_GROUP_ID_ARG=1000 .
```

Run container in interactive mode
```shell
docker run -it --rm -v $(pwd):/var/www/html php74-for-test:1.0.0 sh
```

Inside container run
```shell
php vendor/bin/testbench package:test
```

Or
```shell
php vendor/bin/testbench package:test --coverage
```
