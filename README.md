# laravel-gravitron-sandbox

# Notice
Until this point build and test the EC2 Gravitron from ci/cd is in progress

- [x] check ephemeral EC2 working
- [x] Installed pre-requisites using cloud-init 
- [x] check apache working
- [ ] deploy Laravel code
- [ ] check test cycle working

# Error
```
[2023-12-12 17:10:04] production.ERROR: No application encryption key has been specified. {"exception":"[object] (Illuminate\\Encryption\\MissingAppKe
yException(code: 0): No application encryption key has been specified. at /var/www/vendor/laravel/framework/src/Illuminate/Encryption/EncryptionServic
eProvider.php:79)
```


# Workflow

- to run directly for devs `php artisan serve`

- to build and test the docker container directly
```
docker build -t laravel-web-app .
docker run --rm -d -p 80:80 --hostname testing.com --name laravel-web-app laravel-web-app 
curl http://localhost\?code=OK
docker container logs laravel-web-app | grep "code=OK"
docker container stop laravel-web-app
docker image rm laravel-web-app
```

- to build and test the docker container ci/cd 
    - `git branch release-contatiner` and push

- to build and test the EC2 Gravitron from ci/cd 
    - `git branch release-aws` and push 🚧

