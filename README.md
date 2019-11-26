# cs90
This is the cs90 final project repository

Commands used so far:
  58  mkdir final
   59  cd final
   60  git clone https://github.com/ChadCottle/cs90.git
   61  ls
   62  cd cs90
   63  ls
   64  cat RE*
   65  vi RE*
   66  git status
   67  git add .
   68  git status
   69  git commit -m "First commit"
   70  git push
   71  ssh-key -C cottle.chad@yahoo.com
   72  ssh-keygen -C cottle.chad@yahoo.com
   73  ls
   74  ls ~/.ssh
   75  cat ~/.ssh/id_rsa.pub
   76  ssh-add
   77  sudo ssh-add
KEPT GETTING ERRORS so i found the solution (next two steps) here:
https://coderwall.com/p/rdi_wq/fix-could-not-open-a-connection-to-your-authentication-agent-when-using-ssh-add
   78  ssh-agent
   79  eval $(ssh-agent)
   80  ssh-add
