---
layout: page
title: Setup
---

Git should already be installed on your virtual machine in the DSH. 

Click on `Start` then hover over `Git` to open up `Git Bash`. 

We'll do our work in the `Desktop` folder so make sure you change your working directory to it with:

~~~
$ cd Desktop
~~~
{: .language-bash}

If you type `pwd` (for "print working directory") into Git Bash now you should get back `/n/Desktop`, meaning that you are working in the Desktop on your N drive. 

Now let's create a directory in the `Desktop` folder for our work and then move into that directory:

~~~
$ mkdir planets
$ cd planets
~~~
{: .language-bash}

Then we tell Git to make `planets` a repository -- a place where Git can store versions of our files:

~~~
$ git init
~~~
{: .language-bash}

It is important to note that `git init` will create a repository that
includes subdirectories and their files---there is no need to create
separate repositories nested within the `planets` repository, whether
subdirectories are present from the beginning or added later. Also, note
that the creation of the `planets` directory and its initialization as a
repository are completely separate processes.


[workshop-setup]: https://carpentries.github.io/workshop-template/#git
