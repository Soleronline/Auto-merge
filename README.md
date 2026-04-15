# 🔀 Git Branch Updater Script

A simple Bash script to keep your working branch up to date with the latest changes from the `main` branch.

## 📌 Description

This script automates a common Git workflow by performing the following steps:

1. Detects the current branch you are working on  
2. Switches to the `main` branch  
3. Pulls the latest changes from the remote repository  
4. Switches back to your original branch  
5. Merges `main` into your current branch  

This helps you stay up to date without manually running multiple commands.

---

## ⚙️ Script

```bash
#!/bin/bash

BRANCH=`git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/'`
MAIN='main'

echo -e "\t -> Checkout branch ${MAIN}" \
&& git checkout ${MAIN} \
&& echo -e "\t -> Pulling" \
&& git pull \
&& echo -e "\t -> Checkout to ${BRANCH}" \
&& git checkout ${BRANCH} \
&& echo -e "\t -> Merging" \
&& git merge ${MAIN}
