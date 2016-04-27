# MyReadme
Some general info for setup

# Setting Up Ubuntu in a VM
- Install git
```
sudo apt-get install git
```
- Install Atom editor
```
http GET https://atom.io/download/atom-shell/v0.36.8/node-v0.36.8.tar.gz
```
- Install Atom packages
- - React

## Installing Node and NPM
See https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions
```
curl -sL https://deb.nodesource.com/setup_5.x | sudo -E bash -
```


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
