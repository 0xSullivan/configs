# Create hooks for auto deploy

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
