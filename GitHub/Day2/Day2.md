Day 2 notes

1)git reset

It is used to move the current branch (HEAD) to another commit. Depending on the option, it can also change the staging area and working directory.

    A soft reset moves HEAD to an earlier commit but keeps your changes staged.
        git reset --soft
    
    A hard reset moves HEAD back and discards changes from the staging area and working directory.
        git reset --hard

2)git revert 

It is used to undo the changes made by a previous commit without deleting that commit from history.
Instead of removing the old commit, Git creates a new commit that reverses its changes.
git revert <commit>

3)Reset vs Revert

Git Reset:
- Moves HEAD to an earlier commit.
- Can change or remove commit history.
- Does not create a new commit.
- Useful for local/unpushed commits.
- Can discard changes when using --hard.

Git Revert:
- Does not remove the original commit.
- Creates a new commit that undoes the previous commit.
- Keeps the existing commit history.
- Recommended for commits that are already pushed/shared



WHEN TO USE RESET VS REVERT

Use Git Reset:
- When the commit is local and has not been pushed.
- When you want to rewrite local commit history.
- Example:

git reset --soft HEAD~1


Use Git Revert:
- When the commit has already been pushed to GitHub.
- When working on a shared branch.
- When you want to safely undo a commit without rewriting history.
- Example:

git revert <commit-id>

4) Squash Commit

Squashing commits means combining multiple commits into a single commit.

It is useful for cleaning up commit history before pushing or creating a Pull Request.

INTERACTIVE REBASE

Interactive rebase is commonly used to squash commits.

Command:

git rebase -i HEAD~3

This means:
- Open the last 3 commits for editing.
- We can choose which commits to combine.

WHEN TO USE SQUASH

- To clean up commit history.
- To combine small/fixup commits.
- Before creating a Pull Request.
- To make several related commits appear as one meaningful commit.


5)Cherry Pick

Git cherry-pick is used to apply the changes from a specific commit to the current branch.

It copies the changes introduced by a particular commit and creates a new commit on the current branch.

WHEN TO USE CHERRY-PICK

- When you need one specific change from another branch.
- When you don't want to merge the entire branch.
- To apply a bug fix from another branch.
- To move a specific commit to another branch.

6)Git Rebase 

Git rebase is used to move or reapply commits from one branch on top of another branch.

It creates a cleaner and more linear commit history by changing the base of the branch.

7)Git Merge 

Git merge is used to combine the changes from one branch into another branch.

It joins two branches together and preserves their commit history.

8)Rebase vs Merge

MERGE:
- Combines two branches.
- Preserves existing commit history.
- May create a merge commit.
- Does not rewrite existing commits.

REBASE:
- Reapplies commits on top of another branch.
- Creates a linear history.
- Rewrites commit history.
- Can change commit IDs.

9)SSH KEY SETUP

    1. Generate SSH Key

    ssh-keygen -t ed25519 -C "your-email@example.com"

    Press Enter to accept the default file location.
    Enter a passphrase if required.


    2. Start SSH Agent

    eval "$(ssh-agent -s)"


    3. Add SSH Key to Agent

    ssh-add ~/.ssh/id_ed25519


    4. Copy Public Key

    cat ~/.ssh/id_ed25519.pub

    Copy the entire output.

    5. Add Key to GitHub

    GitHub → Settings → SSH and GPG keys → New SSH key

- Title: Ubuntu/WSL
- Key type: Authentication Key
- Paste the public key
- Click "Add SSH key"


    6. Test Connection

    ssh -T git@github.com

If successful, GitHub will confirm that authentication succeeded.

10)WEBHOOKS

- A webhook is a way for one application to automatically send data to another application when an event occurs.
- It uses an HTTP request, usually POST, to notify the receiving application.
- Example: When code is pushed to GitHub, GitHub sends a webhook to Jenkins to start a build.

Uses of Webhooks

1. CI/CD
- GitHub sends a webhook when code is pushed.
- Jenkins receives it and automatically starts the build/test/deployment process.

2. Notifications
- Sends automatic alerts when an event occurs.
- Example: New GitHub issue → notification sent to Slack or Teams.

3. Integrations
- Connects different applications automatically.
- Example: Payment completed → payment service sends webhook → application updates the order status.

Simple Flow:
Event → Webhook → HTTP Request → Receiving Application → Action




