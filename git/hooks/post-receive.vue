echo "Building assets ... "
git --work-tree=/home/mmd/website --git-dir=/home/mmd/website.git checkout -f
git  --work-tree=/home/mmd/website --git-dir=/home/mmd/website.git pull
echo "Pulling is Done"
echo "Going to project directory"
cd /home/mmd/website
echo "Installing packages ... "
npm i
echo "Building assets ... "
npm run build
echo "Done"
