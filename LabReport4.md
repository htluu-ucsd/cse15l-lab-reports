# Lab Report: Week 7, 11/14/2023, 4-6:00 pm
# Hao Tri Luu

---
## Step 4

First, I logged into the remote account using: `ssh cs15lfa23nq@ieng6-201.ucsd.edu`.
![Image]()

---

## Step 5
Next, I cloned the GitHub repo using: `git clone git@github.com:htluu-ucsd/lab7.git`.
![Image]()

---
## Step 6
Then, I used `cd lab7` to get into the correct working directory and tested the bash script by running `bash test.sh`.
![Image]()

---
## Step 7
After that, I used `vim ListExamples.java` to open the file to edit. Here, I used the following steps:

- `/index1 <enter>` because I knew the bug-inducing code was the variable named `index1`.
- `<shift> #` because I knew where the bug-inducing code was. It took me to the last occurrence of the variable `index1`.
- `e` because I wanted to change the last index from `index1` to `index2`.
- `x` because I wanted to delete the last character `1`.
- `i2` because I wanted to insert a new character `2`.
- `<esc>` because I was done inserting.
- `:wq <enter>` because I wanted to save and exit the file.
![Image]()

---
## Step 8
Once again, I ran `bash test.sh` which hopefully succeeds this time.
![Image]()

---
## Step 9
Seeing that I worked, I want to commit and push the changes to my repository. So I used `git add ListExamples.java` to get it into the staging area. Lastly, I used `git commit` to save my changes and push them into the repository.
![Image]()
