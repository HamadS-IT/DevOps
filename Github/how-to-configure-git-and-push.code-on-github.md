
# How to ``` configure git ``` and  ``` push ``` code on ``` github ```?

### Set Git user configuration
```bash
git config --global user.name "<Your GitHub Username>"
git config --global user.email "<Your GitHub Email>"
```

### Verify Git configuration
```bash
echo "Git User Name: $(git config --global user.name)"
echo "Git User Email: $(git config --global user.email)"
git config --list
```

### Initialize a new Git repository
```bash
git init
```

### Staging a file in local repository
```bash
git add README.md
```

### Checking how many files are in staging area
```bash
git status
```


### Committing the file to the local repository
#### -m option to add a commit message
```bash
git commit -m "<Your Message>"
```

### Renaming the default branch to main 
#### -M option to rename the current branch to 'main'
```bash
git branch -M main
```

### Adding remote repository
```bash
git remote add origin "<Your Repository URL>"
```

### Pushing changes to the remote repository
#### -u option to set the upstream for the main branch
```bash
git push -u origin main
```

