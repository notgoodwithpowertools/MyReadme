# MyReadme
Some general info for setup

# Setting Up Ubuntu in a VM
- Install git
```
sudo apt-get install git
```
- Download Atom editor
```
sudo dpkg -i atom-amd64.deb
```
- Install Atom editor
```
sudo add-apt-repository ppa:webupd8team/atom
```
- Install Atom packages
- atom-beautify, react

## Installing Node and NPM
See https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions
```
curl -sL https://deb.nodesource.com/setup_5.x | sudo -E bash -
```
### Setting Up an Express Server
Set up a share from current project directory
```
var dir =  process.cwd();
console.log('PWDirectory...' + dir);
app.use('/current', express.static(dir + '/public'));
```
node ../../Node/expapp/app.js
PWDirectory.../home/andrew/React/react-node-es6-router
Working directory - /home/andrew/Node/expapp
Example app listening on port...8081
Directory.../home/andrew/Node/expapp




## My useful git commands
Get status
```
git status
```
Add files to the index
```
git add -A
```
Record changes to the repository
```
git commit -m "message"
```
Send the changes to the master and sync
```
git push origin master
```
Create a new local branch "branch_name
```
git checkout -b *branch_name*
```
Restore to a previous known branch state. Prior to the reset (below) delete the node_modules. Then run npm install to rebuild npm environment.
```
git checkout branch_name
git reset --hard branch_name
```
What each commands do:
```
git checkout . - Removes Unstaged Tracked files ONLY [Type 2]
git clean -f - Removes Unstaged UnTracked files ONLY [Type 3]
git reset --hard - Removes Staged Tracked and UnStaged Tracked files ONLY[Type 1, Type 2]
git stash -u - Removes all changes [Type 1, Type 2, Type 3]
```
Download and create a local branch
```
git clone https://github.com/notgoodwithpowertools/react-node-template.git react-node-template
```
Create a new repo and upload local environment
- Go to Github and create new repo
```
git init
git remote -v (view origin and remote)
git remote add origin https://github.com/notgoodwithpowertools/repo name.git
git checkout -b new_branch_name
git push origin new_branch_name
```
If you’re working out of another branch locally, you can either merge to master before pushing, or specify that you want to push your local branch to a remote master. 

# Using Heroku
- Install Heroku Toolbelt - Download toolbelt [toolbelt.heroku.com](http://toolbelt.heroku.com) `$ wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh`
- Install package `heroku`
- To create an Heroku system simply use ```Heroku create```
- To push code ```git push heroku master```
- To push a branch other than master use ```git push heroku ```*yourbranch*```:master```

- If you are recreating a git downloaded project add the heroku remote 
```heroku git:remote -a footy-tips-2```

# Generating a ssh file
```
ssh-keygen -t rsa -b 4096 -C 'email'

git remote set-url origin git@github.com:<Username>/<Project>.git
```
If it is set upfor SSH and you want to temporarily use http(s) use:
```
git push https://github.com/<userid>/<repository> master
```
It should ask you to authenticate

# Installing NVM
Check out https://github.com/creationix/nvm#verify-installation
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash
```
```
nvm install node
```
Or install a specific version...
```
andrew@andrew-virtual-machine:~$ nvm install 8.1.3
Downloading and installing node v8.1.3...
Downloading https://nodejs.org/dist/v8.1.3/node-v8.1.3-linux-x64.tar.xz...
######################################################################## 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v8.1.3 (npm v5.0.3)
Creating default alias: default -> 8.1.3 (-> v8.1.3)
andrew@andrew-virtual-machine:~$ npm --version
5.0.3
andrew@andrew-virtual-machine:~$ npm config get prefix
/home/andrew/.nvm/versions/node/v8.1.3
```
# Verify globally installed npm packages
```
npm list -g --depth=0
```
