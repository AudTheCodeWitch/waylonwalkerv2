---
templateKey: blog-post
path: realistic-git-workflow
title: Realistic Git Workflow
date: 2019-05-27T05:00:00Z
status: Draft
description: My git workflow based on real life.  Its  not always clean and simple.
cover: "/images/yousef-al-nasser-261164-unsplash.jpg"
twitter_cover: "/images/yousef-al-nasser-261164-unsplash-1.jpg"

---
# Realistic Git Workflow

_sometimes things get messy_

## The Clean Path

![](/images/akira-hojo-652732-unsplash.jpg)

**pull 👉 branch 👉 format 👉 work👉 add 👉 commit 👉 pull 👉 rebase 👉 push**

### Pull

As complicated as that seems it is pretty straight forward.  When you sit down to work the first thing you do is to **pull** down the teams latest working "develop" branch from git.

    git checkout develop
    git pull

### Branch

Next create a new branch with a name that will remind you of what you are working on.  For your own sanity choose something descriptive. It is easy to get too many similar branches going and forget which branch is which.

    git checkout -b ingest_product_id_table

### Format

If you know which files in existance that you will be editing before you start work it is a good idea to format them in a commit early on to keep your working commits separate from formatting.  This will make it easier for reviewers to distinguish from your changes and formatting fixes.  

If your team agrees to a consistent formatting logic, sticks to it and always remembers to run the linting/fixing tools you should not have anything to  change.  But thats not what this post is about, its about the real world.  People forget to run linters, some don't care, some may not even be aware of the teams formatting guidelines.  Talk to your team about these things and get on the same page.

I care about formatting, we all should.  We want to put out the best work we can in  our craft.  Realistically though I dont really care about nit picky stuff, I just want things consistant so that it makes things easier to read without me taking the time to swap  out quotes, and fix line spacing. I want a tool to do it for me, and when that tool runs I dont want it mixing in the same commit as my work.

    black .
    git add .
    git commit -m "FIX formatted with black"
    

### Work

Make your changes to your code, test them, document them, clean it up, do what you do best.

### add and commit

Next you will need to stage files that have changed for commit, and commit them.  This can be done in stages to make it clear what the progression was to finish the task you were assigned.

**add all files**
```
    git add .
```

**add a single file**

	git add "path/to/myfile.ext"

**one line commit message**

Here make sure that you create clear messages so that others know.  There are whole posts out there showing how to better write clear commit messages and why you should, check out those posts for more information.

	git commit -m "FEAT ingested product id table on pipeline"

**multi-line commit message**

If you want some more information in your commit message run `git commit` without `-m` and it will pop you into your configured git editor, which is vim by default.

### Super quick vim primer

By default when you run `git commit` you will pop into a vim editor and may want to throw your keyboard before you figure out exactly how to get out of the damn thing.  First type `i` to insert text.  Type out your commit message. Then hit `esc` followed by `:x`.  This is the most basic things you need, and will get you through a commit message.  Vim is a whole topic on its own.

### Integrate your changes

Now that you have made your changes and commited them its time to integrate them into the codebase so that everyone else can see them.  It is likely that time has gone by, and others have made changes to the codebase since you have, so you will want to pull those down first then switch back to your branch.

	git checkout develop
    git pull
    git checkout ingest_product_id_table

Now you have the latest code changes and your work locally.  I prefer to rebase my work with the develop branch, pretending that I started my work after all of the other changes had occurred.  You can choose to merge, but I prefer not to have the extra merge commits in my PR.

	git rebase develop

### push

Now its time to push out to the remote repository and create your PR.

	git push --set-upstream ingest_product_id_table

Open your repository in your web browser and you should see that you have just pushed to a new branch and a  button to open a Pull Request (PR).

### Your Not Done yet

Opening a PR is not a done deal, it starts the conversation to get your code approved to be merged into the develop or master branch.  Your approver may have an idea to clean it up to make it more readable/maintainable, or something to make it more performant.  Remember that a second set of eyes sometimes has a new set of clarity that you do not as you have seen the work from start to end.  At this point they may request changes, discussion, or choose to accept and merge it in.

## Realistically

![](/images/ian-espinosa-177961-unsplash.jpg)