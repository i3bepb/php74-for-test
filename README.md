# Images php for run test

Dockerfiles for create images on php for run test. Images contains installed xdebug, composer. The file **Dockerfile.dev** can be used to run tests locally.

# Build base image

## php 7.4.33

1. Build from root directory
```shell
docker build -f php7433/Dockerfile.base -t i3bepb/php-for-test:1.2.3-php-7.4.33-cli-alpine3.16 .
```

2. Uploading the image to the repository
```shell
docker push i3bepb/php-for-test:1.2.3-php-7.4.33-cli-alpine3.16
```

3. So you can run, check
```shell
docker run --rm -it i3bepb/php-for-test:1.2.3-php-7.4.33-cli-alpine3.16 sh
```

## php 8.0.28

1. Build from root directory
```shell
docker build -f php8028/Dockerfile.base -t i3bepb/php-for-test:1.1.1-php-8.0.28-cli-alpine3.16 .
```

2. Uploading the image to the repository
```shell
docker push i3bepb/php-for-test:1.1.1-php-8.0.28-cli-alpine3.16
```

## php 8.1.16

1. Build from root directory
```shell
docker build -f php8116/Dockerfile.base -t i3bepb/php-for-test:1.0.3-php-8.1.16-cli-alpine3.17 .
```

2. Uploading the image to the repository
```shell
docker push i3bepb/php-for-test:1.0.3-php-8.1.16-cli-alpine3.17
```

## php 8.2.3

1. Build from root directory
```shell
docker build -f php8203/Dockerfile.base -t i3bepb/php-for-test:1.0.2-php-8.2.3-cli-alpine3.17 .
```

2. Uploading the image to the repository
```shell
docker push i3bepb/php-for-test:1.0.2-php-8.2.3-cli-alpine3.17
```

## php 8.2.12

Build from root directory
```shell
docker build -f php8212/Dockerfile.base -t i3bepb/php-for-test:1.1.1-php-8.2.12-cli-alpine3.18 .
```
```shell
docker push i3bepb/php-for-test:1.1.1-php-8.2.12-cli-alpine3.18
```

# How use on local

Build local image with local user (1000:1000)
```shell
docker build -f Dockerfile.dev -t php74-for-test:1.0.0 --build-arg MYAPP_IMAGE=i3bepb/php-for-test:1.2.3-php-7.4.33-cli-alpine3.16 --build-arg LOCAL_USER_ID_ARG=1000 --build-arg LOCAL_GROUP_ID_ARG=1000 .
```

Run container in interactive mode
```shell
docker run -it --rm -v $(pwd):/home/www-data/application php74-for-test:1.0.0 sh
```

Inside container run
```shell
php vendor/bin/testbench package:test
```

Or
```shell
php vendor/bin/testbench package:test --coverage
```
