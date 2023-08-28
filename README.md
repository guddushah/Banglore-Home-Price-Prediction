## Banglore Home Price Prediction with deployment in AWS Cloud EC2 Instance
### This project predicts the Home Prices in Banglore based on the Home's location, size of home in BHK, total square-feet area, and number of bathrooms

- The model was built using sklearn and linear regression using banglore home prices dataset from kaggle.com.
- The python flask server that uses the saved model to serve http requests. 
- The website built in html, css and javascript that allows user to enter home square ft area, bedrooms etc and it calls python flask server to retrieve the predicted price.

### Deploying in EC2 Instance of AWS Cloud
1> Createing an EC2 instance using amazon console, also in security group add a rule to allow HTTP incoming traffic.
2> Connecting with the EC2 Instance using the following commands in Git Bash
  - ssh -i "Banglore_Home_Price.pem" ubuntu@ec2-13-48-42-94.eu-north-1.compute.amazonaws.com   
3> Installing nginx server in EC2 Instance using
  - sudo apt-get update
  - sudo apt-get install nginx
4> Checking the status of nginx
  - sudo service nginx start
  - sudo service nginx status
5> Creating file /etc/nginx/sites-available/bhp.conf
  - server {
    listen 80;
        server_name bhp;
        root /home/ubuntu/Regression/client;
        index app.html;
        location /api/ {
             rewrite ^/api(.*) $1 break;
             proxy_pass http://127.0.0.1:5000;
        }
  }
6> Creating symlink for bhp.conf file in /etc/nginx/sites-enabled
  - sudo ln -v -s /etc/nginx/sites-available/bhp.conf
7> Restaring nginx
  - sudo service nginx restart
8> Installing pip3 and requirements in EC2 Instance
  - sudo apt-get install python3-pip
  - sudo pip3 install -r /home/ubuntu/Regression/requirements.txt
9> Running the server.py
  - python3 /home/ubuntu/Regression/server/server.py

Running the url- ec2-13-48-42-94.eu-north-1.compute.amazonaws.com
  - ![Result](https://github.com/guddushah/Banglore-Home-Price-Prediction/assets/40028193/9d1c5de1-1dd9-456e-b6b7-1cedbf1db68e)





