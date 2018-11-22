# Create hooks for auto deploy

## There is customized file for:
 1. [x] Vue
 2. [ ] Django

## On server
 
    mkdir ~/repo.git
    cd ~/repo.git
    git init --bare

    chmod +x ~/repo.git/hooks/post-receive
    
    git config receive.denyCurrentBranch updateInstead

## ON Client
 

    git remote add live ssh://your_username@your_hostname/~/repo.git
	git push live master
