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
No VM guests are running outdated hypervisor (qemu) binaries on this host.
/var/lib/cloud/instance/scripts/part-001: line 17: docker-php-ext-install: command not found
All settings correct for using Composer
The HOME or COMPOSER_HOME environment variable must be set for composer to run correctly
fatal: destination path '/var/www/html' already exists and is not an empty directory.
/var/lib/cloud/instance/scripts/part-001: line 22: composer: command not found
chmod: cannot access '/var/www/laravel/storage': No such file or directory
chmod: cannot access '/var/www/laravel/bootstrap/cache': No such file or directory
2023-12-12 14:41:00,599 - cc_scripts_user.py[WARNING]: Failed to run module scripts-user (scripts in /var/lib/cloud/instance/scripts)
2023-12-12 14:41:00,599 - util.py[WARNING]: Running module scripts-user (<module 'cloudinit.config.cc_scripts_user' from '/usr/lib/python3/dist-packages/cloudinit/config/cc_scripts_user.py'>) failed
Cloud-init v. 23.2.2-0ubuntu0~22.04.1 finished at Tue, 12 Dec 2023 14:41:00 +0000. Datasource DataSourceEc2Local.  Up 73.54 seconds
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

