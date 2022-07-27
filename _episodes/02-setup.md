---
title: Setting Up Git
teaching: 5
exercises: 0
questions:
- "How do I get set up to use Git?"
objectives:
- "Configure `git` the first time it is used on a computer."
- "Understand the meaning of the `--global` configuration flag."
keypoints:
-   "Use `git config` with the `--global` option to configure a user name, email address, editor, and other preferences once per machine."
---

When we use Git on a new computer for the first time,
we need to configure a few things. Below are a few examples
of configurations we will set as we get started with Git:

*   our name and email address,
*   what our preferred text editor is,
*   and that we want to use these settings globally (i.e. for every project).

On a command line, Git commands are written as `git verb options`,
where `verb` is what we actually want to do and `options` is additional optional information which may be needed for the `verb`. So here is how
Dracula sets up his new laptop:

~~~
$ git config --global user.name "Vlad Dracula"
$ git config --global user.email "vlad@tran.sylvan.ia"
~~~
{: .language-bash}

Please use your own name and email address instead of Dracula's. This user name and email will be associated with your subsequent Git activity,
which means that any changes pushed to the DSH's [GitLab](https://gitlab.com/) instance will include this information.

For this lesson, we will be interacting with [GitLab](https://gitlab.com/) in the DSH and so the email address used should be the same as the one used when setting up your DSH account. 

> ## Line Endings
>
> As with other keys, when you hit <kbd>Enter</kbd> or <kbd>↵</kbd> or on Macs, <kbd>Return</kbd> on your keyboard,
> your computer encodes this input as a character.
> Different operating systems use different character(s) to represent the end of a line.
> (You may also hear these referred to as newlines or line breaks.)
> Because Git uses these characters to compare files,
> it may cause unexpected issues when editing a file on different machines. 
> Though it is beyond the scope of this lesson, you can read more about this issue 
> [in the Pro Git book](https://www.git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#_core_autocrlf).
>
> You can change the way Git recognizes and encodes line endings
> using the `core.autocrlf` command to `git config`.
> The following setting is recommended:
>
> On the DSH Windows desktop:
>
> ~~~
> $ git config --global core.autocrlf true
> ~~~
> {: .language-bash}
> 
> And on Linux (e.g. if you are configuring Git for use on the DSH HPC cluster):
>
> ~~~
> $ git config --global core.autocrlf input
> ~~~
> {: .language-bash}
> 
{: .callout}

Dracula may also want to set his favorite text editor, using one of the commands on this table (nano is the default):

| Editor             | Configuration command                            |
|:-------------------|:-------------------------------------------------|
| nano               | `$ git config --global core.editor "nano -w"`    |
| Vim                | `$ git config --global core.editor "vim"`   |
| VS Code                | `$ git config --global core.editor "code --wait"`   |

It is possible to reconfigure the text editor for Git whenever you want to change it.

Git (2.28+) allows configuration of the name of the branch created when you
initialize any new repository.  Dracula decides to use that feature to set it to `main` so 
it matches the cloud service he will eventually use. 

~~~
$ git config --global init.defaultBranch main
~~~
{: .language-bash}

> ## Default Git branch naming
>
> Source file changes are associated with a "branch." 
> For new learners in this lesson, it's enough to know that branches exist, and this lesson uses one branch.  
> By default, Git will create a branch called `master` 
> when you create a new repository with `git init` (as explained in the next Episode). This term evokes 
> the racist practice of human slavery and the 
> [software development community](https://github.com/github/renaming)  has moved to adopt 
> more inclusive language. 
> 
> In 2020, most Git code hosting services transitioned to using `main` as the default 
> branch. As an example, any new repository that is opened in GitHub and GitLab default 
> to `main`.  However, Git has not yet made the same change.  As a result, local repositories 
> must be manually configured have the same main branch name as most cloud services.  
> 
> For versions of Git prior to 2.28, the change can be made on an individual repository level.  The 
> command for this is in the next episode.  Note that if this value is unset in your local Git 
> configuration, the `init.defaultBranch` value defaults to `master`.
>
{: .callout}

The five commands we just ran above only need to be run once: the flag `--global` tells Git
to use the settings for every project, in your user account, on this computer.

You can check your settings at any time:

~~~
$ git config --list
~~~
{: .language-bash}

You can change your configuration as many times as you want: use the
same commands to choose another editor or update your email address.

> ## Enabling Secure Channel 
>
> Finally, you need to tell Git that the DSH uses Secure Channel rather than OpenSSL
> for its HTTPS certificates. If you're not sure what this means, don't worry - but if you 
> see an `Unable to get local issuer certificate` error message as you work your way through
> this course it may be that you missed this step!
>
> ~~~
> $ git config --global http.sslBackend schannel
> ~~~
> {: .language-bash}
{: .callout}

> ## Git Help and Manual
>
> Always remember that if you forget the subcommands or options of a `git` command, you can access the
> relevant list of options typing `git <command> -h` or access the corresponding Git manual by typing
> `git <command> --help`, e.g.:
>
> ~~~
> $ git config -h
> $ git config --help
> ~~~
> {: .language-bash}
>
> While viewing the manual, remember the `:` is a prompt waiting for commands and you can press <kbd>Q</kbd> to exit the manual.
>
> More generally, you can get the list of available `git` commands and further resources of the Git manual typing:
>
> ~~~
> $ git help
> ~~~
> {: .language-bash}
>
{: .callout}

[git-privacy]: https://help.github.com/articles/keeping-your-email-address-private/
