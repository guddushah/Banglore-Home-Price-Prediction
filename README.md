## Banglore Home Price Prediction with deployment in AWS Cloud EC2 Instance
### This project predicts the Home Prices in Banglore based on the Home's location, size of home in BHK, total square-feet area, and number of bathrooms

We first build a model using sklearn and linear regression using banglore home prices dataset from kaggle.com.
Second step would be to write a python flask server that uses the saved model to serve http requests. 
Third component is the website built in html, css and javascript that allows user to enter home square ft area, bedrooms etc and it will call python flask server to retrieve the predicted price.

### Deploying in EC2 Instance of AWS Cloud
1> Createing an EC2 instance using amazon console, also in security group add a rule to allow HTTP incoming traffic.

2> Connecting with the EC2 Instance using the following commands in Git Bash
  - ssh -i "Banglore_Home_Price.pem" ubuntu@ec2-13-48-42-94.eu-north-1.compute.amazonaws.com
  - 
3> Installing nginx server in EC2 Instance using
  - sudo apt-get update
  - sudo apt-get install nginx
