---
title: "Supplemental: Using Git from RStudio"
teaching: 10
exercises: 0
questions:
- "How can I use Git with RStudio?"
objectives:
- "Understand how to use Git from RStudio."
keypoints:
- "Using RStudio's Git integration allows you to version control a project over time."
---

Version control can be very useful when developing data analysis scripts. For
that reason, the popular development environment
[RStudio][rstudio] for the R programming language has built-in
integration with Git. While some advanced Git features still require the
command-line, RStudio has a nice interface for many common Git operations.

RStudio allows us to create a [project][rstudio-projects] associated with a
given directory to keep track of various related files. To be able to track the
development of the project over time, to be able to revert to previous
versions, and to collaborate with others, we version control the Rstudio
project with Git. To get started using Git in RStudio, we create a new project:

![RStudio screenshot showing the file menu dropdown with "New Project..." selected](../fig/RStudio_screenshot_newproject.png)

This will open a dialog asking us how we want to create the project. We have
some options here. Let's say that we want to use RStudio with the planets
repository that we already made. Since that repository lives in a directory on
our computer, we choose the option "Existing Directory":

![RStudio screenshot showing New Project dialog window with "Create project from existing directory" selected](../fig/RStudio_screenshot_existingdirectory.png)

Next, RStudio will ask which existing directory we want to use. Click
"Browse..." and navigate to the correct directory, then click "Create Project":

![](../fig/RStudio_screenshot_navigateexisting.png)

Ta-da! We have created a new project in RStudio within the existing planets
repository. Notice the vertical "Git" menu in the menu bar. RStudio has
recognized that the current directory is a Git repository, and gives us a
number of tools to use Git:

![RStudio window after new project is created with large arrow pointing to vertical Git menu bar.](../fig/RStudio_screenshot_afterclone.png)

To edit the existing files in the repository, we can click on them in the
"Files" panel on the lower right. Now let's add some additional information
about Pluto:

![](../fig/RStudio_screenshot_editfiles.png)

Once we have saved our edited files, we can use RStudio to commit the changes
by clicking on "Commit..." in the Git menu:

![RStudio screenshot showing the Git menu dropdown with "Commit..." selected](../fig/RStudio_screenshot_commit.png)

This will open a dialogue where we can select which files to commit (by
checking the appropriate boxes in the "Staged" column), and enter a commit
message (in the upper right panel). The icons in the "Status" column indicate
the current status of each file. Clicking on a file shows information about
changes in the lower panel (using output of `git diff`). Once everything is the
way we want it, we click "Commit":

![](../fig/RStudio_screenshot_review.png)

> ## Did RStudio guess your username and email address?
>
> Frustratingly, RStudio in the DSH may not be able to find the file containing the 
> Git configuration settings you created in the [setup episode](02-setup.md). To fix
> this, you can open up the "Terminal" tab and work through the list of configuration
> options again, e.g. `git config --global user.email "vlad@tran.sylvan.ia"`. 
{: .callout}

The changes can be pushed by selecting "Push Branch" from the Git menu. There
are also options to pull from the remote repository, and to view the commit
history:

![RStudio screenshot showing the git menu dropdown with "History" selected](../fig/RStudio_screenshot_history.png)

> ## Are the Push/Pull Commands Grayed Out?
>
> Grayed out Push/Pull commands generally mean that RStudio doesn't know the
> location of your remote repository (e.g. on GitLab). To fix this, open a
> terminal to the repository and enter the command: `git push -u origin
> main`. Then restart RStudio.
{: .callout}

If we click on "History", we can see a graphical version of what `git log`
would tell us:

![](../fig/RStudio_screenshot_viewhistory.png)

RStudio creates a number of files that it uses to keep track of a project. We
often don't want to track these, in which case we add them to our `.gitignore`
file:

![RStudio screenshot showing .gitignore open in the editor pane with the files .Rproj.user, .Rhistory, .RData, and \*.Rproj added to the end](../fig/RStudio_screenshot_gitignore.png)

> ## Tip: versioning disposable output
>
> Generally you do not want to version control disposable output (or read-only
> data). You should modify the `.gitignore` file to tell Git to ignore these
> files and directories.
{: .callout}

> ## Challenge
>
> 1. Create a new directory within your project called `graphs`.
> 2. Modify the `.gitignore` so that the `graphs` directory is not version controlled.
>
>
> > ## Solution to Challenge
> >
> > This can be done in Rstudio:
> > ```
> > dir.create("./graphs")
> > ```
> > {: .language-r}
> > Then open up the `.gitignore` file from the right-hand panel of Rstudio and add 
> > `graphs/` to the list of files to ignore.
> {: .solution}
{: .challenge}

There are many more features in the RStudio Git menu, but these should be
enough to get you started!


[rstudio]: https://www.rstudio.com/
[rstudio-projects]: https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects
