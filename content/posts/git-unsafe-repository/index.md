---
title: "Git Unsafe Repository"
date: 2022-04-24
draft: false
categories:
  - Tech Tips
tags: 
  - git
  - windows
author: Sachin Ganpat
summary: 'What to do when you get the error "fatal: unsafe repository (<repo directory is owned by someone else)"'
cover:
    image: "images/Git-logo.png" # image path/url
    alt: "Git Logo" # alt text
    # caption: "<text>" # display caption under cover
    relative: true# when using page bundles set this to true
    hidden: false # only hide on current single page
editPost:
    URL: "https://github.com/essgeelabs/essgeelabs/tree/master/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

Yesterday I tried a `git status` on one of my repositories and got the error:

```
fatal: unsafe repository ('C:/Users/sganpat/Website/essgeelab.net' is owned by someone else)
To add an exception for this directory, call:

        git config --global --add safe.directory C:/Users/sganpat/Website/essgeelab.net
```

This is linked to the [fix for CVE-2022-24765 and CVE-2022-24767](https://github.blog/2022-04-12-git-security-vulnerability-announced/) and shows up after Git version 2.35.2.

One fix is to run the command:

```
git config --global --add safe.directory <directory of git repository>
```

However, in my case, I needed to update the owner of the folder.

Right-Click on the root folder of the repository in Windows Explorer and click on "Properties".

Select the "Security" tab and click on "Advanced".

![Security Tab](images/01.png)


At the "Owner" line, you should see someone other than yourself as the owner. Click on "Change".

![Advanced Properties](images/02.png)


Select yourself as the owner and click "Ok". Select "Replace owner on subcontainers and objects" and click "Ok" out of all the dialog boxes.

![Replace the Owner](images/03.png)


Now Git should be working fine again in your repository. Try doing a `git status`.

```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

