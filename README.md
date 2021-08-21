# Getting started with Django and AWS Elastic Beanstalk

## Requirement

- python3
- pip3
- virtualenv

## Step 1: Clone and install dependencies

```shell
git clone https://github.com/vovantamvn/gs-beanstalk.git
cd gs-beanstalk
virtualenv venv
source ./venv/bin/activate
pip install -r requirements.txt
```

## Step 2: Configure EB

Install awsebcli, in my case I install global

```shell
deactivate
pip install awsebcli
```

## Step 3: Create an application

```shell
eb init
```

- Select a default region: 7 (In my case I choose Singapore)
- Enter aws-access-id & aws-secret-key: (You can see
  this [article](https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html))
- Enter Application Name:
- Select a platform branch: 1 (It's recommended)
- Do you wish to continue with CodeCommit? (Y/n): n
- Do you want to set up SSH for your instances?: y (You can choose y to create a ssh key, and then you can access the
  instance.)

## Step 4: Create an environment

```shell
eb create
```

- Enter Environment Name:
- Enter DNS CNAME prefix: (When you deploy an app to Elastic Beanstalk you will automatically get a domain name like
  xxx.elasticbeanstalk.com. DNS CNAME prefix is what you want to be used in place of xxx.)
- Select a load balancer type: 2

Read my config in [.ebextensions/django.config](.ebextensions/django.config)

## Step 5: Terminate the environment

You can terminate the environment when you don't need it.

```shell
eb terminate
```
