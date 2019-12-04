# This is the cs90 final project repository <br/>

**Install and configure git**<br/>
For this project I launched an aws linux ec2 instance and sshed to it.<br/>
Note: this could be installed locally on a mac or windows machine.<br/>
mkdir final <br/>
cd final <br/>
<br/>
Create an ssh public and private key pair for use with github.com<br/>

ssh-keygen -C *email address*  <br/>
ls ~/.ssh <br/>
cat ~/.ssh/id_rsa.pub <br/>
<br/> 
`ssh-add` KEPT GETTING ERRORS so i found the solution (next two steps) [here:](https://coderwall.com/p/rdi_wq/fix-could-not-open-a-connection-to-your-authentication-agent-when-using-ssh-add) <br/>
<br/>
`ssh-agent` <br/>
`eval $(ssh-agent)` <br/>
`ssh-add` <br/>
<br/>
Next create a github account and add your public key to it (*id_rsa.pub*)<br/>
<br/>

Install git using:  `sudo yum git install -y`<br/>

Then initialize git:  `git init`<br/>

Then configure git:

`$ git config --global user.name "John Doe"`<br/>
`$ git config --global user.email johndoe@example.com`<br/>

Create a repository in your github.com with a README.md file.<br/>

Then clone it to the local machine (in our case ec2)<br/>
git clone git@github.com:ChadCottle/cs90.git <br/>
cd cs90 <br/>
cat README.md <br/>
<br/>
Open up README.md and make some changes in markdown language.<br/>
vi README.md <br/>

git status <br/>
git add . <br/>
git status <br/>
git commit -m "First commit" <br/> 
git push<br/>
<br/>
## Create Roles first<br/>

First we will create some IAM roles.<br/>
We need a role for our ec2 instance(s) and a role for the Code Deploy service.<br/>

1. Create a role called CDInstanceRole<br/>
Attach the following policies:<br/>
**AmazonEC2RoleforAWSCodeDeploy**<br/>
**AutoScalingNotificationAccessRole**<br/>

2. Create a role called CDServiceRole
Attach the following policy:<br/>
**AWSCodeDeployRole**<br/>
**Note:** on the Trust Relationship tab you will need to edit this line:<br/>
`”Service": “ec2.amazonaws.com”` and change it to the following: `”Service": “codedeploy.amazonaws.com"`<br>

## Create our initial ec2 instance that will run our web application<br/>
Choose a region that will run an instance as well as CD and CP<br/>
Launch a simple aws linux app within a VPC’s public subnet<br/>
Auto-assign a public IP<br/>
Choose our IAM role that was created earlier for instances: *CDInstanceRole*<br/>


Under Advanced Details add the following in the user data section:<br/>
`#!/bin/bash`<br/>
`sudo yum update -y`<br/>
`sudo yum install httpd -y`<br/>
`sudo yum install ruby -y`<br/>
`wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install`<br/>
`chmod +x ./install`<br/>
`sudo ./install auto`<br/>
`sudo service httpd start`<br/>
`sudo chkconfig httpd on`<br/>

Here’s what is going on with the user data section.  We are doing a standard update followed by installing apache (httpd).
We then install ruby and wget the codedeploy agent and codedeploy resource kit from a bucket in our region. The bucket choices are listed [here.](https://docs.aws.amazon.com/codedeploy/latest/userguide/resource-kit.html#resource-kit-bucket-names)
Then we make it executable and install it.  And lastly we are starting Apache and setting it to come back up after a reboot.<br/>

## Code Deploy and Code Pipeline<br/>
<br/>
Here is where we get into the meet of our project.  We will follow these general steps for **Code Deploy** <br/>
1. Create an **application** <br/>
2. Create a **deployment group** <br/>
3. Create a **deployment** <br/>

Before starting we need to create a [Personal Access Token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) in our github.com account. 

For this section we will also use the **AWSCodeDeployRole** we created earlier.

