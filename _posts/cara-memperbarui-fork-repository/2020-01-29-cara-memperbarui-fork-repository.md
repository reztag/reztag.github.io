---
layout: post
title: How to update a forked repo the complicated way
date: 2020-01-29 01:00 +0700
modified: 2020-03-07 16:49:47 +07:00
description: There are two ways to update a forked repository using the web interface provided by GitHub, which is complicated, or through the terminal, which is even more complicated.
tag:
  - tips
  - git
  - software
image: /cara-memperbarui-fork-repository/repo.png
---

Starting from wanting to update an old repo from an organization, I intended to refactor it. It turns out there are updates from the original repo, so I decided to write an article about it. Here's a rough illustration:

<figure>
<img src="{{ page.image }}" alt="illustration of the repo to be updated">
<figcaption>Fig 1. The complexity of the process.</figcaption>
</figure>

There are two ways to update a forked repository using the web interface provided by GitHub, which is complicated, or through the terminal, which is even more complicated.

### Through Github (the boring way) 💻

1. Open the forked repository on GitHub.
2. Click on **Pull Requests** on the right side, then click **New Pull Request**.
3. It will show the comparison between the upstream repository and your forked repository. If it says "There isn't anything to compare," click on the link **switching the base**, which will reverse your forked repository to become the base repository and the upstream repository as the head repository.
4. Click **Create Pull Request**, provide a title for the pull request, and click **Send Pull Request**.
5. Click **Merge Pull Request** and **Confirm Merge**.

\* _Make sure you don't make any changes to the forked repo, so that the merge can be done automatically, otherwise there might be conflicts._

### Through terminal ⌨️

Add the remote address of the original repository here and name it `upstream`. Replace `ORIGINAL_OWNER` and `ORIGINAL_REPO` with the address of your original repository.

```bash
$ git remote add upstream git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git
$ git remote -v
> origin    git@github.com:yourusername/yourrepo.git (fetch) # forked repo
> origin    git@github.com:yourusername/yourrepo.git (push) # forked repo
> upstream    git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git (fetch) # upstream repo / original repo
> upstream    git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git (push) # upstream repo / original repo
```

Checkout ke local branch `master`.

```bash
$ git checkout master
> Switched to branch 'master'
```
If you're done, merge the local repo with the remote `upstream/master`.

```bash
$ git merge upstream/master
```

Finally, push the local repo to the remote `origin`.

```bash
$ git add -A
$ git commit -m "updating origin repo" && git push -u origin master
```

Good luck with this complicated method, hopefully it can be understood. Personally, I prefer using the terminal. If there's something complicated, why not look for an easier way.

##### Resources

- [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)
- [Update your fork directly on Github](https://rick.cogley.info/post/update-your-forked-repository-directly-on-github/#top)
