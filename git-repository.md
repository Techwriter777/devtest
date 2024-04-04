# Git Repository

## Introduction

During the CI process, the application source code is pulled from your git repository.

Devtron also supports multiple git repositories (be it from one Git account or multiple Git accounts) in a single deployment.

Therefore, this doc is divided into 2 sections, read the one that caters to your application:

* [Single Repo Application](broken-reference)
* [Multi Repo Application](broken-reference)

***

## Single Repo Application

Follow the below steps if the source code of your application is hosted on a single Git repository.

In your application, go to **App Configuration** → **Git Repository**. You will get the following fields and options:

1. [Git Account](broken-reference)
2. [Git Repo URL](broken-reference)
3. (Checkboxes)
   * [Exclude specific file/folder in this repo](broken-reference)
   * [Set clone directory](broken-reference)
   * [Pull submodules recursively](broken-reference)

### Git Account

This is a dropdown that shows the list of Git accounts added to your organization on Devtron. We recommend you to first add your Git account (especially when the repository is private).

{% hint style="info" %}
If the authentication type of your Git account is anonymous, only public Git repositories in that account will be accessible. Whereas, adding a user auth or SSH key will make both public and private repositories accessible.
{% endhint %}

### Git Repo URL

In this field, you have to provide your code repository’s URL, for e.g., `https://github.com/devtron-labs/django-repo`.

You can find this URL by clicking on the 'Code' button available in your repository page as shown below:

![](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/creating-application/git-material/repo-url.jpg)

{% hint style="info" %}
* Copy the HTTPS/SSH portion of the URL too
* Make sure you've added your [Dockerfile](https://docs.docker.com/engine/reference/builder/) in the repo
{% endhint %}

### Exclude specific file/folder in this repo

If you enable this, you can define the file(s) or folder(s) whose commits you wish to exclude/include from the list of commits shown to you before you initiate a CI build.

In other words, if a given commit contains changes in file(s) present in your exlusion rule, the commit won't show up while selecting the material, which means it will not be eligible for build.

![Figure 1: Excludes commits made to README.md](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/creating-application/git-material/excluded-commit.jpg)

Devtron allows you to create either an exlusion rule, inclusion rule, or a combination of both. In case of multiple files or folders, you can list them in new lines.

To exclude a file, use **!** as the prefix, e.g. `!filename`\
To include a file, don't use any prefix, e.g. `filename`

You may use the **Learn how** button (as shown below) to understand the syntax of defining an exclusion or inclusion rule.

![Excludes commits made to README.md](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/creating-application/git-material/rules.jpg)

#### Examples

*   **Exclusion of a single file (e.g. README.md)**

    ```
    !README.md
    ```

    Commits containing changes made in only `README.md` file will not be shown
*   **Exclusion of multiple files (e.g. README.md, index.js)**

    ```
    !README.md
    !index.js
    ```

    Commits containing changes made in only `README.md` or/and `index.js` file will not be shown
*   **Inclusion of a single file (e.g. README.md)**

    ```
    README.md
    ```

    Commits containing changes made in only `README.md` file will be shown. Rest all will be excluded.
*   **Exclusion of a single folder and all its files (e.g. src)**

    ```
    !src/*
    ```

    Commits containing changes made in only `src` folder will not be shown
*   **Exclusion and inclusion of files (e.g. README.md, index.js)**

    ```
    !README.md
    index.js
    ```

    Commits containing changes made in `README.md` will not be shown, but commits made in `index.js` file will be shown. All other commits apart from the aforementioned files will be excluded.
*   **Exclusion and inclusion of conflicting files**

    ```
    !README.md
    README.md
    ```

    If conflicting paths are defined in the rule, the one defined later will be considered. In this case, commits containing changes made only in `README.md` will be shown.

Since file paths can be long, Devtron supports regex too for writing the paths. To understand it better, you may click the `How to use` link as show below.

![](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/creating-application/git-material/regex-help.jpg)

### Set clone directory

After clicking the checkbox, a field titled `clone directory path` appears. It is the directory where your code will be cloned for the repository you specified in the previous step.

This field is optional for single git repository application and you can leave the path as default. Devtron assigns a directory by itself when the field is left blank. The default value of this field is `./`

![](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/creating-application/git-material/clone-directory.jpg)

### Pull submodules recursively

This checkbox is optional and is used for pulling [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) present in a repo. The submodules will be pulled recursively, and the auth method used for the parent repo will be used for submodules too.

***

## Multi Repo Application

As discussed earlier, Devtron also supports multiple git repositories in a single application. To add multiple repositories, click **Add Git Repository** and repeat all the steps as mentioned in [Single Repo Application](broken-reference). However, ensure that the clone directory paths are unique for each repo.

Repeat the process for every new git repository you add. The clone directory path is used by Devtron to assign a directory to each of your Git repositories. Devtron will clone your code at those locations and those paths can be referenced in the Docker file to create a Docker image of the application.

Whenever a change is pushed to any the configured repositories, CI will be triggered and a new Docker image file will be built (based on the latest commits of the configured repositories). Next, the image will be pushed to the container registry you configured in Devtron.

{% hint style="info" %}
Even if you add multiple repositories, only one image will be created based on the Dockerfile as shown in the docker build config
{% endhint %}

### Why do you need Multi-Git support?

Let’s look at this with an example:

Due to security reasons, you want to keep sensitive configurations like third party API keys in separate access-restricted git repositories, and the source code in a git repository that every developer has access to. To deploy this application, code from both the repositories are required. A Multi-Git support helps you achieve it.

Other examples where you might need Multi-Git support:

* To make code modularized, where front-end and back-end code are in different repos
* Common library extracted out in a different repo so that other projects can use it
