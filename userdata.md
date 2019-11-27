`#!/bin/bash<br/>
sudo yum update -y<br/>
sudo yum install httpd -y<br/>
sudo yum install ruby -y<br/>
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install<br/>
chmod +x ./install<br/>
sudo ./install auto<br/>
sudo service httpd start<br/>
sudo chkconfig httpd on`<br/>
