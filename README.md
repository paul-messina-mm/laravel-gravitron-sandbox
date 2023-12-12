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
Loading composer repositories with package information
Updating dependencies
Deprecation Notice: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/Composer/DependencyResolver/Problem.php:366
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - spatie/laravel-ignition[2.0.0, ..., 2.3.1] require ext-curl * -> it is missing from your system. Install or enable PHP's curl extension.
    - Root composer.json requires spatie/laravel-ignition ^2.0 -> satisfiable by spatie/laravel-ignition[2.0.0, ..., 2.3.1].
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

