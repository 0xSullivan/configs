# Create hooks for auto deploy

## There is customized file for:
 1. [x] Vue
 2. [x] Django

## On server
 
    mkdir /home/server/repo.git
    cd /home/server/repo.git
    git init --bare

    chmod +x /home/server/repo.git/hooks/post-receive
    
    git config receive.denyCurrentBranch updateInstead

## ON Client
 

    git remote add live ssh://your_username@your_hostname/~/repo.git
	git push live master
