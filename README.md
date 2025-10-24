DevOps Version Control Project (VCP)

Project Objective

This repository documents a complete, best-practice workflow for managing a small DevOps project using Git, demonstrating Gitflow principles, Conventional Commits, and release tagging. This guide serves as a tutorial to replicate the exact steps taken to build the project's history.

 Phase 1: Setup and Initialization

This phase creates the local repository, adds essential configuration files, and pushes the base structure to GitHub.

Action

Command

Why We Do This

1. Create Project Directory

mkdir devops-vcp && cd devops-vcp

Creates a new project folder and moves the terminal into it. All subsequent commands run inside this folder.

2. Initialize Git

git init

Initializes Git tracking. This creates the hidden .git folder, turning the directory into a Git repository.

3. Create Essential Files

(Manually add the required README.md and .gitignore content)

The .gitignore prevents unnecessary files (like build logs, temp files, or dependency folders) from being accidentally saved in your commit history.

4. Stage All Files

git add .

Prepares all new and changed files (README.md, .gitignore, etc.) to be included in the next saved snapshot (commit).

5.  Connect to Remote

git remote add origin <YOUR_GITHUB_REPO_URL>

Links your local folder to the repository you created on GitHub (the remote destination).

6. Initial Commit

git commit -m "feat(init): initial project setup and documentation"

Saves the first version of the project permanently. We use the feat prefix to signify adding a new, foundational feature (the project itself).

7. Push Main Branch

git branch -M main

It Renames your local master branch to main to match the remote.

git push -u origin main

Uploads the initial commit and the main branch to GitHub. The -u flag sets the upstream tracking, simplifying future push commands.

Phase 2: Branching and Feature Development

We create isolated branches (dev and feature) to prevent unstable code from affecting the stable, production-ready branch.

Action as

Command

Why We Do This

1. Create Development Branch

git checkout -b dev

Creates the primary integration branch, dev, which branches directly off of main. All features will first merge into dev for stabilization.

2. Push dev to Remote

git push -u origin dev

Shares the dev branch structure with the rest of the team on GitHub.

3. Start Feature Work

git checkout -b feature/user-profile-endpoint

Creates a specific, short-lived branch for the task. This ensures work on the profile feature is completely isolated.

4. Add Feature Code

echo "# User Profile Code" > profile.js

Simulates the act of writing the actual code for the new feature. This file holds the new work we want to save.

5. Stage Feature File

git add profile.js

Tells Git to include the new profile.js file in the next save.

6. Commit Feature Work

git commit -m "feat(profile): implement basic profile retrieval logic"

Saves the progress on the isolated feature branch. We use feat(scope) to describe the new functionality.

7. Push Feature to Remote

git push -u origin feature/user-profile-endpoint

Uploads the branch and its commits to GitHub. This makes the feature ready for review.

Phase 3: Integration via Pull Request (PR)

This is the code review step, which happens directly on the GitHub website.

Action

Steps (on GitHub)

Why We Do This

1. Create Pull Request (PR)

GO TO GITHUB: Create a PR from feature/user-profile-endpoint to dev.

A PR is a formal request for code review. It's where teammates check code quality, confirm tests pass, and discuss changes before they are merged into the shared dev line.

2. Merge PR

(After approval, merge the PR on GitHub.)

Integrates the profile feature code into the main development branch, dev.

3. Clean Up Local dev

git checkout dev
git pull origin dev

checkout dev switches your local terminal back to the integration branch. git pull downloads the merged changes from GitHub to synchronize your local branch.

4. Delete Local Branch

git branch -d feature/user-profile-endpoint

Deletes the local feature branch. It is no longer needed since the work is merged and safe in dev.

Phase 4: Release and Tagging

The final promotion of stable code from dev to the official production branch (main), followed by marking the code with a version number.

Action

Command

Why We Do This

1. Final PR for Release

GO TO GITHUB: Create a PR from dev to main.

This signifies that the code in dev is considered stable, tested, and ready for deployment to production.

2. Merge PR

(After final approval, merge the PR on GitHub.)

Makes the new features official by integrating them into the production branch (main).

3. Update Local main

git checkout main
git pull origin main

Switches to the main branch and downloads the final, merged release code.

4. Create Release Tag

git tag -a v1.0.0 -m "Release Candidate 1: Initial deployment with profile feature"

Attaches a lightweight, permanent label (v1.0.0) to the exact commit used for the production release. This helps in auditing or rolling back if needed.

5. Push Tag to Remote

git push origin v1.0.0

Uploads the tag to GitHub, making the official release marker visible to all users.
