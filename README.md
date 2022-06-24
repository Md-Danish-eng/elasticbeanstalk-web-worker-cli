# Deploy python_flask App on Elasticbeanstalk

Create a ubuntu server

Create an IAM user and give permission to that user i gave Administrator Access permission.

Install AWS cli by following this doc

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions

Install EBCLI by following this doc

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html

Then run aws configure command provide the Access_key and Secret_Access_key and choose the region

Then colne the github repo https://github.com/devops-team-poc/elasticbeanstalk-web-worker-cli.git 

Go to the clone directory and change the directory to signup-webserver using the command: ```cd signup-webserver``` 

then run eb init and fil the requirements and this run eb create and fill the details here

Wait for sometime and Go to Elasticeanstalk console and check there is one Application and webserver environment is created 

Note: The signup-webserver directory has a file named iam_policy.json. Copy this policy to the attached IAM role so that the instance can access Dynamo

DB and SNS Services.

copy the url of Elasticbeanstalk and paste in your browser you will saw 

Then go to signup-worker directory and type eb init 

After this go to AWS console < Elasticbeanstalk 

you will find there is one Application name signup-worker click on this and create Enviroment 

select worker environment.
 
``` source venv/staging-LQM1lest/bin/activate ```


((staging) ) [root@ip-172-31-14-207 app]# pip freeze

boto==2.48.0
click==6.7
Flask==1.0
gunicorn==20.1.0
itsdangerous==0.24
Jinja2==2.10.1
MarkupSafe==2.0.1
Werkzeug==2.0.1

((staging) ) [root@ip-172-31-14-207 app]# cat current/requirements.txt 

boto==2.48.0
click==6.7
Flask==1.0
itsdangerous==0.24
Jinja2==2.10.1
Werkzeug==2.0.1

Note: make sure that MarkupSafe version should be 2.0.1 if not then install by using following command: 

pip install MarkupSafe==2.0.1

then run flask run

cp ../app.config

export FLASK_APP=application.py
export APP_CONFIG=app.config

flask run

after this if app is not openining then go to /etc/nginx/conf.d/elasticbeanstalk/00_application.conf  and change the port from 8000 to 5000 

then nginx -t  and systemctl restart nginx and check
