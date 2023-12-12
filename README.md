# laravel-gravitron-sandbox

# Notice
Until this point build and test the EC2 Gravitron from ci/cd is in progress

- [x] check ephemeral EC2 working
- [x] Installed pre-requisites using cloud-init 
- [x] check apache working
- [x] deploy Laravel code
- [ ] check test cycle working

# Project status 🚥

- 🟢 No errors 

```
curl http://54.191.98.63/?code=OK
Laravel Information
Host: 54.191.98.63
HTTP Query: code=OK
Date: 2023-12-12 17:20:26
PHP Version: 8.2.13
Laravel Version: 10.36.0
APP_ENV: local
```

## Next Steps
- [ ] improve the test to check expected output (for example: HTTP Query: code=OK )
  - [ ] in the output
  - [ ] in the logs
- [ ] install NewRelic agent 
- [ ] add End-2-End test based in puppeteer
- [ ] Study how to create VPC, Security Group, Subnet 
- [ ] Be able to deploy in other (faster) regions 

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
