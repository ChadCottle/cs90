`#!/bin/bash
sudo yum update -y
sudo yum install httpd -y
sudo yum install ruby -y
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service httpd start
sudo chkconfig httpd on`
