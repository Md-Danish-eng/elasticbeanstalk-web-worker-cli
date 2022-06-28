# Deploy python_flask App on Elasticbeanstalk

# To understand Web server environments follow this doc.

```https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-webserver.html```

# To understand Worker environments follow this doc.

```https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-worker.html```

### Create a ubuntu server

### Create an IAM user and give permission to that user i gave Administrator Access permission.

### Install AWS cli by following this doc

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions

### Install EBCLI by following this doc

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html

### Then run aws configure command provide the ``` Access_key and Secret_Access_key ```  and choose the region

Then colne the github repo https://github.com/devops-team-poc/elasticbeanstalk-web-worker-cli.git 

### Go to the clone directory and change the directory to signup-webserver using the command: ```cd signup-webserver``` 

### then run eb init and fil the requirements and this run eb create and fill the details here

### Wait for sometime and Go to Elasticeanstalk console and check there is one Application and webserver environment is created 

### Note: The signup-webserver directory has a file named iam_policy.json. Copy this policy to the attached IAM role so that the instance can access Dynamo

### DB and SNS Services.

### copy the url of Elasticbeanstalk and paste in your browser you will saw 

### Then go to signup-worker directory and type eb init 

### After this go to AWS console < Elasticbeanstalk 

### you will find there is one Application name signup-worker 

![image](https://user-images.githubusercontent.com/85988020/175870531-15cd5c20-598e-42e6-ac6d-9d89fd38828b.png)

### click on this and choose worker Enviroment

![image](https://user-images.githubusercontent.com/85988020/175870766-dd590f13-d1a8-47a2-a75d-05ca6c454f4e.png)

### Choose python in the platform section and go with sample application in Application code and click on configure more options

![image](https://user-images.githubusercontent.com/85988020/175871067-d30d4860-27fa-4cef-a654-a42226a6c039.png)

###  Click the Edit button in the worker section.
 
 ![image](https://user-images.githubusercontent.com/85988020/175871700-fa612712-5d52-4678-955b-a274df9b9b17.png)

### Select the queue existing queue generated by the signup-webserver and save.

![image](https://user-images.githubusercontent.com/85988020/175871909-ca584d40-dc09-4491-a3b3-2f918620d427.png)

### Go to Security section and edit 

![image](https://user-images.githubusercontent.com/85988020/175872030-bbaf6dec-2234-4826-b304-beb212278b5c.png)

### Choose key-pair if you want to login in the instance.

![image](https://user-images.githubusercontent.com/85988020/175872191-dd5dcd70-c098-438e-81cb-eaa74a9aa3b3.png)

### After configuration, click the Create environment button.

![image](https://user-images.githubusercontent.com/85988020/175874769-9db2b0bd-7998-4088-a802-617a0dcc5748.png)

### It took sometime to create all the things. Go to the dynamodb and SNS and check there is table and topic created or not, check your email and confirm the subscription.

![image](https://user-images.githubusercontent.com/85988020/175939556-3d25c3ef-2a51-490b-8d85-a180be9ee042.png)

### Go to the server and run the following commands to site up

``` source venv/staging-LQM1lest/bin/activate ```

((staging) ) [root@ip-172-31-14-207 app]# ``` pip freeze ```

boto==2.48.0
click==6.7
Flask==1.0
gunicorn==20.1.0
itsdangerous==0.24
Jinja2==2.10.1
MarkupSafe==2.0.1
Werkzeug==2.0.1

((staging) ) [root@ip-172-31-14-207 app]# ``` cat current/requirements.txt ```

boto==2.48.0
click==6.7
Flask==1.0
itsdangerous==0.24
Jinja2==2.10.1
Werkzeug==2.0.1

# Note: make sure that MarkupSafe version should be 2.0.1 if not then install by using following command: 

``` pip install MarkupSafe==2.0.1 ```

then run ``` flask run ```

``` cp ../app.config ```

```export FLASK_APP=application.py ```

``` export APP_CONFIG=app.config ```

``` flask run ```

### after this if app is not openining then go to ``` /etc/nginx/conf.d/elasticbeanstalk/00_application.conf ``` and change the port from 8000 to 5000 

then ``` nginx -t ```  and ``` systemctl restart nginx ``` and check by hit the url of elasticbeanstalk.

![image](https://user-images.githubusercontent.com/85988020/175936927-16dc14dc-a606-4993-8dfd-0218f4d8106f.png)

![image](https://user-images.githubusercontent.com/85988020/175937058-80f1a31b-926f-4a00-b930-b76363002db7.png)

![image](https://user-images.githubusercontent.com/85988020/175937213-f297de9d-d322-4b95-a0e7-fc6aef96db66.png)


# HAPPY LEARNING!!!





