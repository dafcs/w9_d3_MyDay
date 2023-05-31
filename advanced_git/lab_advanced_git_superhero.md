# Advanced Git

## Learning Objectives

- Know Git naming conventions
- Be able to create and move between branches
- Understand the difference between implicit and explicit merges
- Be able to merge branches and resolve merge conflicts
- Be able to use pull requests to merge branches
- Be able to apply Git hygiene
- Be able to use Git as part of a team

## Introduction

We have been using GitHub as a versioning tool to enable us to go back to previous version of our code. Git has a feature called branching that allow us to create parallel versions of our projects, so as to ensure we always have a stable version readily available. GitHub also has a whole host of features that allows developers to collaborate on projects, working on the code simultaneously.

## Git's Main Branch

Until now we have been working on one branch, the 'main' branch. In a Git initialised directory, you will see the word 'main' after the directory name in the terminal. This is the default branch that is created when we create a Git repository. (whether local or remote)

Until now, every time you have been committing your changes, you have been committing to main. You have then been able to use git commands to go back to a previous version of your code. One problem with this process is that it can be difficult to find the commit relating to the version you want to go back to. Branches help with this problem.

## Git Branches

With branches, once we have a stable version of a program committed to git and we are about to add a new piece of functionality or refactor the code in some way, we can create a new branch. This creates a copy of the code. The new branch will be in the same state as the branch you branched off. Now you can work in the new branch, adding your new feature or refactoring, knowing that you have a stable version back on the original branch should you decide to abandon the feature or you decide the refactor wasn't an improvement.

### Typical Branch Naming Conventions and Use Cases

Permanent Branches:

- "main" is the name of the default branch. This should always contain stable working code. Merging code into the main might involve -
  - Before the merge: Creating a Pull Request to get others to review and approve the merge into main
  - After the merge: Triggering CI / CD steps such as -
    - running automated tests 
    - linting code for consistent formatting
    - detecting security vulnerabilities in packages (aka dependencies)
    - deploying the code to production if all our checks pass

Temporary Branches:

- Feature branches are used to develop new functionality. The naming convention is 'feature/name_of_feature'. These branches are deleted after the feature is integrated back into main.
- Fix branches are used to fix a bug. There are different conventions, but you can use a prefix to indicate its purpose like, 'fix/name_of_fix'. These branches are deleted after the fix is integrated back into main.

Pushing to temporary branches may also involve some of the checks above for main (excluding production deployment!). In addition there may be deployments to staging or test environments to support automated and manual testing.

## Git Merging and Conflicts

When we merge two branches together, we integrate the code from one into the other. For example, when we have completed the feature on the feature branch we want and integrate the code into the main branch. Sometimes Git can do the integration process automatically for us, but when there have been changes made on both branches, Git may not know which lines to keep and which to discard, and we have to do it manually. This is called a merge conflict. This is a common problem when working collaboratively, where different people are working on different branches simultaneously and learning how to handle them is an important part of learning how to use Git.

The principle of merging branches is to first merge the stable branch (e.g. main) into the potentially unstable branch (e.g. feature) so that any conflicts can be dealt with and fixes made there. Once you are sure your feature branch is stable, you then merge it into main. This ensures the stable branch remains stable.