# Git and GitHub initial setup

Docs.microsoft.com has content in several repositories. Once you know the repository to which you will be contributing, you need to do some first time setup. 

<video width="640" height="360" controls poster="./media/git-and-github-repository-initial-setup/git-and-github-initial-setup.png">
  <source src="http://video.ch9.ms/ch9/eab1/d9bebd59-bc3d-4aa8-8aa2-86fc2d92eab1/gitrepositorysetup_mid.mp4" type="video/mp4">
  <a href="http://video.ch9.ms/ch9/eab1/d9bebd59-bc3d-4aa8-8aa2-86fc2d92eab1/gitrepositorysetup_mid.mp4">
    <img src="./media/git-and-github-repository-initial-setup/git-and-github-initial-setup.png" alt="Git and GitHub Initial Setup">
  </a>
</video>

## Create a fork of the repository in GitHub

When you first start contributing to a repository, you need to “fork” it. A fork is your personal copy of a repository in GitHub. Think of it as your sandbox on GitHub. When you fork the main repository, you get a copy of all the branches in your fork. 

1. Navigate to the repository's main GitHub page and click the *Fork* button in the upper right. 
2. If prompted, select your GitHub account as the destination where the fork should be created. This creates a copy of the repository within your GitHub account. 

![GitHub profile example](./media/tools-and-setup/fork.png)

> Note: **You only need to fork one time** per repository. All the following steps need to be done per computer.

## Clone a copy of the forked repository to your computer

Next you need to *clone* a local copy of your fork. Cloning creates a local copy of a repository on your computer. When you clone, it will copy the master branch from your forked repository into a directory on you local computer.

Be sure to **clone your fork** not the Microsoft repository.  Otherwise, you won’t be able to contribute changes. The main repository is referenced with the organization name Microsoft `github.com/Microsoft/repo-name`. Your fork is referenced using your GitHub user name `github.com/GitHubUsername/repo-name`.

The clone command performs several actions. It will create a directory on the local file system, initialize the local repository, and copy all the files from the master branch. Clone also sets up a remote alias called *origin* that points to your forked repository. 

Cloning is a one time per computer operation.  If you get a new PC, you’ll need to clone your fork to your new machine.

The Git clone command requires GitHub credentials. There are several ways to cache credentials. You can provide credentials using Git Credential Manager for Windows, Git credential helper, or you can use a GitHub personal access token for each GitHub request. 
- On Windows, you can use Git Credential Manager. Git Credential manager will allow you to enter your GitHub credentials once for a computer rather than using your personal access token each time you clone a repository. 
- On MacOS and Linux, you can use Git credential helper, please see [Caching your GitHub password in Git](https://help.github.com/articles/caching-your-github-password-in-git/#platform-all).
- GitHub personal access tokens can be used on any platform. However, you need to configure per repository.

### Option 1: Authenticate using GitHub credentials with Credential Manager or credential helper.

1. Launch the Git enabled command prompt.
2. At the command prompt, enter the following command, which will create a directory on your computer using the same as specified in `<repository-name>`. 

> Tip: You can get your fork's GitHub URL for the clone command from the "Clone or download" button in the GitHub UI. ![Clone or download](./media/git-and-github-repository-initial-setup/clone-or-download.png)

```
        git clone https://github.com/<your GitHub user name>/<repository-name>.git
```
For example, this clone command could look something like this:
```
        git clone https://github.com/smithj/IntuneDocs.git  
```

3. When prompted, enter your GitHub credentials.
   - For Windows Credential Manager, use your GitHub user name and password.
   - For Git credential helper, use your GitHub user name and personal access token as the password.

If you're using the default location, your local copy of the repository will be stored in your user's home directory.

Since you are caching credentials, skip ahead to the [Set remote for upstream repository](#set-remote-for-upstream-repository) section.

### Option 2: Authenticate using a GitHub Personal Access Token

1. Copy the Personal Access Token that you got from [https://github.com/settings/tokens](https://github.com/settings/tokens). You likely saved your personal access token when you set up your GitHub account.
2. Launch the Git enabled command prompt. For example, on Windows use *Git bash*, on MacOS use *terminal*, on Linux use *bash* shell.
3. At the command prompt, enter the following command, which will create a directory on your computer using the same as specified in `<repository-name>`. 

   ```
   git clone https://[your GitHub user name]:[token]@github.com/<your GitHub user name>/<repository-name>.git
   ```
For example, this clone command could look something like this:
   ```
   git clone https://smithj:b428654321d613773d423ef2f173ddf4a312345@github.com/smithj/IntuneDocs.git  
   ```

> Note: Since the clone command also configures the remote for "origin", your access token will be saved as part of the remote.

If you're using the default location, your local copy of the repository will be stored in `<your user account>\<repository-name>`.

## Set remote for upstream repository

In order to sync the latest changes from the Microsoft repository you also need to set up a remote alias called *upstream* that points to the Microsoft repository. Use the `git remote` command. Note that the `clone` command you used above automatically created a "remote" alias to your forked repository. We will also use the `fetch` command to get branch info from the "upstream" repository for later use.

If using a credential helper, use the following commands:
```
        cd <repository-name>
        git remote add upstream https://github.com/Microsoft/<repository-name>.git
        git fetch upstream
```
If using a **GitHub personal access token**, use the following commands:
```
        cd <repository-name>
        git remote add upstream https://[your GitHub user name]:[token]@github.com/Microsoft/<repository-name>.git
        git fetch upstream
```

This may take some time to complete. 

After you complete this section, you won't have to fork again or enter your credentials again. You would only have to clone the forks to a local computer again if you install Git on another computer.

## Next steps
- [Minor contributions](./minor-contributions.md) 
- Back to [contributors guide](./index.md)

<!--Anchors-->

[Fork the repository and copy it to your computer]: #fork-the-repository-and-copy-it-to-your-computer
[Install git-credential-winstore]: #install-git-credential-winstore
[Configure your user name and email locally]: #configure-your-user-name-and-email-locally