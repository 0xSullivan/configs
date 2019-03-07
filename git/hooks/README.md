# Create hooks for auto deploy

## There is customized file for:
 1. [x] Vue
 2. [x] Django

## On server
 
    mkdir ~/.git
    cd ~/.git
    git init --bare
---
.git/post-receive

    workTree=/home/mmd/apartech/website
	gitDir=/home/mmd/apartech/website/.git
	git --work-tree=$workTree --git-dir=$gitDir checkout -f
	git  --work-tree=$workTree --git-dir=$gitDir pull origin master
	echo "Pulling is Done"
---
    chmod +x ~/repo.git/hooks/post-receive
    
    git config receive.denyCurrentBranch updateInstead

## ON Client
 

    git remote add live ssh://root@ip/.../.git
	git push live master
