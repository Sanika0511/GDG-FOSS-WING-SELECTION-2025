### Answer the following questions in you own words.

> It's not necessary that you havee to know and answer all the questions. Just answer the ones
> you know and write in your own words.

1. Give the difference between the remotes - upstream and origin - with an example.

You answer: 
origin is the name given to your fork (your copy of the repository).
upstream is the original repository from which you forked.

for e.g;
You fork github.com/org/project → your fork is origin.
The original github.com/org/project → is upstream.

2. You have two branches A and B and you have currently made some changes in branch A.
You want to move into branch B but do not want to commit the current changes in branch A.
What will you do?

You answer: I will use git stash. This saves my uncommitted changes temporarily
git stash
git checkout B
Later, if I return to branch A, I can bring my changes back using git stash pop.

3. You were assigned a work to implement a feature and create a PR to your organization's remote repository.
For this you made a branch (say A) and made some changes and commited them. Now you moved to some other branch 
(say B) to do some other assigned work. But later you realisd that have to complete the task assigned earlier 
first and commited some changes in branch B which are meant for branch A. How will you use git to bring the 
changes from branch B to branch A?

You answer:

3. What is the difference between fetching changes and pulling changes?

Your answer: git fetch only downloads the changes from the remote repository but doesn’t apply them to your current branch.

git pull is fetch + merge. It downloads the changes and also updates your current branch.

4. What does -i flag stand for? What is it's significance in git?

You answer: -i stands for interactive.
For example, git rebase -i HEAD~3 lets you rewrite, squash, or reorder commits interactively. It is useful when cleaning up commit history before making a pull request.

5. You are working in an organization that follows very strict guidelines for PRs and commits.
You made three commits in your PR and the maintainer says you were supposed to make a single commit.
What will you do in this case?

You answer: I will use interactive rebase to squash the commits into one:
git rebase -i HEAD~3
Then choose squash for the last two commits so that all three become one. Finally, force-push the branch.

6. Explain `git merge` and `git rebase` with example(s).

You answer: Merge: Combines changes from one branch into another and creates a merge commit.
for e.g:
git checkout main
git merge feature
Main now has feature’s changes but with a separate merge commit.

Rebase: Re-applies commits of one branch on top of another, creating a linear history.
for e.g:
git checkout feature
git rebase main
Now feature branch looks like it was created from the latest main, no extra merge commit.

7. Write the flow how you create a repository and push changes to it. Also mention the commands used at each step.

You answer: 
git init                           # initialize repo
git remote add origin <url>        # add remote
git add .                          # add files
git commit -m "Initial commit"     # commit changes
git branch -M main                 # rename branch to main
git push -u origin main            # push to GitHub


8. How would you prevent a file or folder from getting tracked by git?

Your answer: You create a file called .gitignore in the main folder of your project.
Anything you put in that file's list—like a secrets.js file or a node_modules folder—will be completely ignored by Git. It's the most common way to keep private keys or large dependencies out of your repo

9. You did not implement the step you mentioned in question 8 and now you have committed and pushed your database's
secret key to the github. How will you remove the key from your git's commit history to avoid any misuse?

You answer: I will use git filter-repo (recommended) or git filter-branch to rewrite history and remove the secret. 
for e.g:
git filter-repo --path config.json --invert-paths
git push origin --force
After that, I will rotate/regenerate the secret key to ensure safety.

---