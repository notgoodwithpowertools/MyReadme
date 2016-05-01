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
sudo dpkg -i atom-amd64.deb
```
- Install Atom packages
- React

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
What each commands do:
```
git checkout . - Removes Unstaged Tracked files ONLY [Type 2]
git clean -f - Removes Unstaged UnTracked files ONLY [Type 3]
git reset --hard - Removes Staged Tracked and UnStaged Tracked files ONLY[Type 1, Type 2]
git stash -u - Removes all changes [Type 1, Type 2, Type 3]
```
