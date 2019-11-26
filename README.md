This is the cs90 final project repository
Commands used so far: 
mkdir final
cd final 
ssh-keygen -C cottle.chad@yahoo.com
ls ~/.ssh 
cat ~/.ssh/id_rsa.pub 
ssh-add KEPT GETTING ERRORS so i found the solution (next two steps) here: 
https://coderwall.com/p/rdi_wq/fix-could-not-open-a-connection-to-your-authentication-agent-when-using-ssh-add 
ssh-agent 
eval $(ssh-agent) 
ssh-add
git clone git@github.com:ChadCottle/cs90.git
ls 
cd cs90
ls 64 
cat README.md
vi README.md 
git status 
git add . 
git status 
git commit -m "First commit" 
git push
