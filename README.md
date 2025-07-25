# MyReadme
Some general info for setup

# Setting Up Ubuntu in a VM
- Installing VMware tools
Seems that while open-vm-tools is installed (after the fast install) it doesn't work very well. It can be made to work ok so you don't have to install the packaged version - check
https://www.itechlounge.net/2019/08/linux-copy-paste-not-working-between-vmware-workstation-host-and-debian-guest/
```
sudo apt-get autoremove open-vm-tools

sudo apt-get install open-vm-tools-desktop
```
From https://github.com/vmware/open-vm-tools/issues/54
```
sudo apt-get install --reinstall open-vm-tools-desktop
```
This gets the screen resizing working after install. Also, deselect/reselect shared folders and this enabled this function
- Install git
```
sudo apt-get install git
```
Install packages from Snap
- Gimp
- VS Code
```
sudo snap install --classic code
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

### Ubuntu network interface issues
If the network interface disappears from the GUI try
```
$ sudo nmcli networking off
$ sudo nmcli networking on
```
or better
```
sudo systemctl restart NetworkManager.service
```

## My useful git commands
Rename main branch
```
git branch -m master main
```
Check default branch name
```
git config --global init.defaultBranch main
```
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
1) First set the remote using the github key
2) Push changes

```
git remote set-url origin https://REPLACE-WITH-TOKEN@github.com/REPLACE-WITH-USERNAME/REPLACE-REPO-NAME.git/
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
or, clone a specific branch
```
git clone --branch <branchname> <remote-repo-url>
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
First install curl
```
sudo apt-get install curl

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

# Baseline App Framework
## Create React App
```
npx create-react-app <app_name>
```
### Install packages
```
npm install --save react react-dom redux react-redux redux-thunk react-router-dom moment

npm install --save firebase@4.12.1

npm install --save-dev redux-devtools-extension firebase-admin
```
To test
```
npm run start
```
### Firebase Hosting Config
```
npm install -g firebase-tools
```

For Firebase hosting, first initialize Firebase
```
firebase init
```
Select hosting
Directory is 'build'
To deploy
```
npm run build
firebase deploy
```
Config options
```
What do you want to use as your public directory? public
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? File public/index.html already exists. Overwrite? No
i  Skipping write of public/index.html

=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? build
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? File build/index.html already exists. Overwrite? No
i  Skipping write of build/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...

✔  Firebase initialization complete!
```

# If hot reloading doesn't work after install in fresh Ubuntu
```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
https://github.com/webpack/docs/wiki/troubleshooting#not-enough-watchers

# Copy working files to backup using rsync
```
rsync -av --no-perms --no-owner --no-group --mkpath --exclude '*/node_modules' /home/andrew/Code/ /mnt/hgfs/andrew/Downloads/codebackup/U-2204-Code3-14-12-22
```

## Firebase Cloud Functions & CORS

Best most useful article I could find ...

https://haha.world/firebase-cors/

# Installing Java into Ubuntu
```
$ sudo apt install default-jre
openjdk version "17.0.10" 2024-01-16
OpenJDK Runtime Environment (build 17.0.10+7-Ubuntu-123.10.1)
OpenJDK 64-Bit Server VM (build 17.0.10+7-Ubuntu-123.10.1, mixed mode, sharing)
```
# Getting Ubuntu sound working in Fusion VM
https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting#stuttering-audio-in-virtual-machine
```
mkdir -p ~/.config/wireplumber/wireplumber.conf.d/
cd ~/.config/wireplumber/wireplumber.conf.d
```
```
monitor.alsa.rules = [
  {
    matches = [
      # This matches the value of the 'node.name' property of the node.
      {
        node.name = "~alsa_output.*"
      }
    ]
    actions = {
      # Apply all the desired node specific settings here.
      update-props = {
        api.alsa.period-size   = 1024
        api.alsa.headroom      = 8192
      }
    }
  }
]
```
## Persisting the emulator state

But there is a simple solution to that problem. After adding some users you can export your emulator’s state via firebase emulators:export <export-directory>. So the next time you start your emulators, simply use firebase emulators:start --import <export-directory> and all your precious previous configuration is restored. Phew!

`firebase emulators:export <export-directory>`. So the next time you start your emulators, simply use firebase emulators:start --import <export-directory> and all your precious previous configuration is restored. Phew!

```firebase emulators:start --import <export-directory> --export-on-exit <export-directory>``` 

https://medium.com/@doaschdn/how-to-persist-your-data-with-firebase-emulators-567403a59394

## Installing Ubuntu VM on ARM
# Linux VM Setup
- Enable folder sharing
```
sudo apt-get install open-vm-tools 
sudo apt-get install open-vm-tools-desktop
```
# Get audio working
```
https://www.reddit.com/r/vmware/comments/1dq4t32/ubuntu_vm_on_vmware_fusion_pro_1352_having_issues/
```
# Install nvm and Node
# [Install VSCode 64bit ARM](https://code.visualstudio.com/docs/?dv=linuxarm64_deb)
- Setup Copilot



