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
/var/lib/cloud/instance/scripts/part-001: line 22: composer: command not found

and
  Problem 1
    - symfony/css-selector is locked to version v7.0.0 and an update of this package was not requested.
    - symfony/css-selector v7.0.0 requires php >=8.2 -> your php version (8.1.2) does not satisfy that requirement.
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

