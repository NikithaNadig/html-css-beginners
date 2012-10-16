---
layout: default
title: Your first repository
---

# Your first repository

{% highlight sh %}
$ git init myfirstrepo
Initialized empty Git repository in /tmp/myfirstrepo/.git/
{% endhighlight %}

Git creates a directory called `myfirstrepo`, this is where you'll be keeping all
your code. Then git creates a subdirectory called `.git` which is where it keeps
all the settings and history for this repository. It starts with a dot, which means
that it is a hidden directory, to keep it out of the way of your files.

So at the moment, you have a completely blank repository that is ready to add
files. From now on, your command line will need to be inside `myfirstrepo` so
that git knows which repository to use. The `status` command in git will let you
know this current status of your repository:

{% highlight sh %}
$ cd myfirstrepo
$ git status
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
{% endhighlight %}

## Add a file

We can put any type of file into Git. It is especially good at keeping track of
text files such as Python, Javascript, HTML and CSS. A very common file is the
README, which is used to tell people what the repository is about.

Create a new file called `README` inside `myfirstrepo/` with your text editor.
You can put any text inside here. Maybe you would like something a little
mysterious? We could put some Keats in here:

    Here will I kneel, for thou redeemed hast
    My life from too thin breathing: gone and past
    Are cloudy phantasms. Caverns lone, farewel!
    And air of visions, and the monstrous swell
    Of visionary seas! No, never more
    Shall airy voices cheat me to the shore
    Of tangled wonder, breathless and aghast.

Yes, this seems suitable.

Once you have the file saved then it's time to add it to your repository. In
git, you add and remove files with the `add` and `rm` commands.

{% highlight sh %}
$ git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README
nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}

Here git is saying that the README file is not being tracked. Let's add it.

{% highlight sh %}
$ git add README
$ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   README
#
{% endhighlight %}

Ok, it's in. Now we can create our first commit. A commit is a snapshot of the
repository at a particular point in time. Everything that we `add` counts
towards the next commit.

For now we just want the new README file in our commit. So let's commit it:

{% highlight sh %}
$ git commit -m "This is my first commit."
[master (root-commit) 199b7a1] This is my first commit.
 1 file changed, 7 insertions(+)
 create mode 100644 README
{% endhighlight %}

And `log` will tell us that the commit is now in the repository:

{% highlight sh %}
$ git log
commit 199b7a1457ebd5c1df3cb5fde21a45b769d9c31c
Author: Steven Farlie <steven.farlie@gmail.com>
Date:   Mon Oct 15 15:01:26 2012 +0200

    This is my first commit.
{% endhighlight %}

Git has saved a snapshot of your repository at the moment you committed. If you
will take a look at `git status` it will tell you that your directory is
currently 'clean', meaning that nothing has changed since the commit. You can
always return your directory back to any commit in your history. Likewise, you
can also fast-forward your directory to commits in your future, for example when
somebody has made a change that you would like to add to your repository. But
we'll get to that later when we discuss pulling changes from others.

## Extra fun

You can add more and more commits to your repository using the same "add commit"
workflow. Try adding an attribution to the README (it's John Keats from the poem
[Endymion](http://www.gutenberg.org/ebooks/24280)), or adding some source files
of your own to the repository, and committing a few changes here and there.

# Pushing to GitHub

Now that we have this fantastic local repository, it's time to change the world
by sharing it on GitHub!

Fortunately, the process is pretty simple. We'll create a repository on GitHub
using the exact same name, then copy our repository to GitHub.

* Create a repository called 'myfirstrepo' on the [new repository
  page](https://github.com/new). Leave all the options as default.

Now see the section *Push an existing repository from the command line*. It
has the two key commands you'll need, tailored for your repository.

* *git remote add* associates your local repository to your GitHub repository,
  which will be called _origin_ (which is a git convention for the default
  remote repository). You could also call it _github_ or _upstream_ or anything
  you like, as it only applies to your local repository.
* *git push* pushes commits to _origin_ (GitHub) from the branch _master_ (the
  default branch). The `-u` option tells git that we want _origin_ as the
  default in future, so we don't have to type it every time.

# Streamlining the process

Now that you've done it the manual way, you should know that it can be a little
easier than this. If you know at the beginning that you want to share your code
on GitHub, you can just [create a new repository](https://github.com/new), check
"Initialize this repository with a README" and `clone` the repository, like so:

{% highlight sh %}
$ git clone git@github.com:stevenfarlie/myfirstrepo.git
Cloning into 'myfirstrepo'...
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0)
Receiving objects: 100% (3/3), done.
{% endhighlight %}

Everything will be set up for you, with an initial README commit and _origin_
pointing to GitHub. If you use a graphical tool like GitHub for Mac it can be
even easier, as it will put a "Clone" button directly on GitHub website so you
don't even have to type `git clone`. These are all shortcuts for the same basic
process that you went through.