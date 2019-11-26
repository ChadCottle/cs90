**This is the cs90 final project repository** <br/>
Commands used so far: <br/>
mkdir final <br/>
cd final <br/>
ssh-keygen -C *email address*  <br/>
ls ~/.ssh <br/>
cat ~/.ssh/id_rsa.pub <br/>
<br/> 
ssh-add KEPT GETTING ERRORS so i found the solution (next two steps) here:<br/> 
https://coderwall.com/p/rdi_wq/fix-could-not-open-a-connection-to-your-authentication-agent-when-using-ssh-add <br/> 
`ssh-agent` <br/>
`eval $(ssh-agent)` <br/>
`ssh-add` <br/>
git clone git@github.com:ChadCottle/cs90.git <br/>
ls <br/> 
cd cs90 <br/>
ls <br/>
cat README.md <br/>
vi README.md <br/>
git status <br/>
git add . <br/>
git status <br/>
git commit -m "First commit" <br/> 
git push<br/>

