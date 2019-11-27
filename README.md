**This is the cs90 final project repository** <br/>

**Install and configure git**<br/>
For this project I launched an aws linux ec2 instance and sshed to it.<br/>

mkdir final <br/>
cd final <br/>
<br/>
Create an ssh public and private key pair for use with github.com<br/>

ssh-keygen -C *email address*  <br/>
ls ~/.ssh <br/>
cat ~/.ssh/id_rsa.pub <br/>
<br/> 
ssh-add KEPT GETTING ERRORS so i found the solution (next two steps) here:<br/>
https://coderwall.com/p/rdi_wq/fix-could-not-open-a-connection-to-your-authentication-agent-when-using-ssh-add <br/>
<br/>
`ssh-agent` <br/>
`eval $(ssh-agent)` <br/>
`ssh-add` <br/>
<br/>
Next create a github account and add your public key to it (*id_rsa.pub*)<br/>
<br/>

Install git using:  `sudo git install -y`<br/>

Then initialize git:  `git init`<br/>

Then configure git:

`$ git config --global user.name "John Doe"`<br/>
`$ git config --global user.email johndoe@example.com`<br/>

Create a repository in your github.com with a README.md file.<br/>

Then clone it to the local machine (in our case ec2)<br/>
git clone git@github.com:ChadCottle/cs90.git <br/>
ls <br/> 
cd cs90 <br/>
ls <br/>
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


