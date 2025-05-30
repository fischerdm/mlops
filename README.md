# mlops
This repository stores useful information about MLOps. It can be used as a scaffold to CI/CD.

## Setting up the Git Credential Manager

## Installing or upgrading git (over homebrew)
Before setting up the Git Credential Manager (CDM) we have to install or upgrade. We use homebrew here.

### Updating and upgrading homebrew
In the context of Homebrew, updating means fetching the latest list of available packages and versions from the Homebrew repository. This command updates Homebrew itself and the list of available formulas (packages). It ensures that your local package list is synchronized with the latest versions available in the Homebrew repository.

Upgrading with Homebrew means installing newer versions of the packages you already have installed on your system. This command upgrades all outdated packages to their latest versions based on the updated package list.

Run first 
```bash
brew update
```
and then
```bash
- brew upgrade
```

### Git
Next we can either install or upgrade git

```bash
brew upgrade git
````
```bash
brew install git
```

### Git configuration

In case you choose the https option to clone a repository, there's the possiblity to store your credentials. Let's configure the Git Credential Manager (GCM) for that.

First check your current Git configuration settings using the following command:

```bash
git config --global --list
```
Remove all existing credential helper configurations

```bash
git config --global --unset-all credential.helper
```

Set the desired credential helper
```bash
git config --global credential.helper /usr/local/share/gcm-core/git-credential-manager
```
Verify the configuration
```bash
git config --global --list | grep credential.helper
```

**On MacOS, you may have to update your KeyChain with the Credentials for GitHub (or GitLab).**

## PAT (Classic)

### Github

Here's a brief overview of some common scopes and their purposes on Github:
- **repo**: Full control of private repositories. This is the most commonly used scope for general Git operations.
- **repo:status**: Read-only access to commit statuses.
- **repo_deployment**: Access to manage deployment environments.
- **admin:repo_hook**: Read and write access to repository hooks.
- **workflow**: If you need to manage GitHub Actions workflows, this scope is necessary. It allows you to read, write, and manage workflows in your repositories.
- **write:packages**: For reading and writing packages published to GitHub Packages.
- **delete_repo**: For deleting repositories.

#### Extended Scope that should meet most needs.

**repo**:
Full control of private repositories: This scope allows you to read, write, and manage repository contents, including code, commit statuses, and pull requests. It's essential for performing most Git operations.

#### Optional Scopes
Depending on your specific needs, you might also consider adding the following scopes:

**admin:repo_hook**: If you need to manage repository hooks, this scope allows you to read and write repository hooks.

**workflow**: If you are involved in managing GitHub Actions workflows, this scope allows you to manage workflows.

**write:packages**: If you need to interact with GitHub Packages, this scope allows you to read and write packages.

### Implementation
To implement a restriction in GitHub so that no one can directly push to the main or master branch, you need to set up branch protection rules. Here's a step-by-step guide to doing this:
1) Navigate to Your Repository:
    Go to the main page of the repository on GitHub.

2) Access Repository Settings:
    Click on the "Settings" tab near the top right of the repository page.

3) Branches Section:
    In the left sidebar of the Settings page, find and click on the "Branches" option. This is typically under the "Code and automation" section.

4) Add Branch Protection Rule:
    Click on the "Add rule" button. If you already have rules set up, you might see an "Add branch protection rule" button instead.

5) Specify Branch Name:
	In the "Branch name pattern" field, enter the name of the branch you want to protect. For example, type main or master.

6) Configure Protection Settings:
	- Require a pull request before merging: Enable this option to ensure that all changes must go through a pull request.
	- Require approvals: You can specify the number of approvals required before a pull request can be merged.
	- Require status checks to pass before merging: You can specify which status checks must pass before merging.
	- Include administrators: Decide whether to include administrators in these restrictions.
	- Restrict who can push to matching branches: You can restrict pushes to specific users, teams, or apps if needed.

7) Save Changes:
	After configuring the settings to your preference, click the "Create" or "Save changes" button to apply the branch protection rule.

By setting up these branch protection rules, you ensure that all changes to the main or master branch must go through a pull request, thereby preventing direct pushes and enhancing code quality and collaboration.

You have to give this token a name for instance *General Repository Access and Workflow*.

### GitLab

tbd.

