##The Git Guide for Mac Users
_Easy-to-follow instructions for using the version control system_

###Overview

#####What is Git?

Git is a tool that allows you to keep track of multiple versions of a project. At any point in modifying the file, you can use Git to view earlier versions, view changes made along the way, and even revert to one of those earlier versions. Let’s say you’ve created a résumé that you’ve organized chronologically, but you’re thinking about using a skills-based organization instead. You could create a second file, copy the information from the original file and paste it into the new file, then save the file under a name like “Skills-based Resume.docx.” This can become tedious and, more than likely, you’ll end up with several files with inconsistent naming patterns, and a poorly organized workstation. 

Instead of creating new files, you can simply “commit” (or save) the file to Git at certain milestones. Once you’ve committed the résumé that is organized chronologically, feel free to add or delete text and move sections around. If you don’t like the new pattern, use Git to revert to the previous version. 
















2. Your email address:

   	**git config --global user.email [jdoe@somewhere.com]**
	
3. The editor, or the application you may use when typing messages in Git:

	**git config --global core.editor [name]**
	
	*At times, you will have to compose brief messages for Git. You may find a plain text editor helpful for these instances. There are a few applications that work in conjunction with Terminal: Pico, emacs, vi, and nano. Though they are all very similar to one another, nano may be the most user-friendly and is the text editor of choice for this tutorial.
	
To check that you’ve correctly entered your settings, use the command **git config –list**. 
For a reference list of commands, simply type **git help**.

The final step for setting up Git will take place in your Finder window. You will need to create a folder that will house the documents you plan to use with Git. It’s most convenient to store this folder in your home folder. When naming folders and files, try to limit the name to 1-2 words. Omit spaces in between words if possible: the shorter the name, the more quickly you can type commands. Lastly, Git commands are case sensitive, so using all lower-case names might save time as well.

#####The Stages of a Project

A project will go through a basic three-step process in Git. It may be easier to understand this process by starting with the final stage, where Git takes a snapshot of the file in its current state and “commits” (or saves) that version to its directory. This is the _commit_ stage. Prior to this step, you have made changes to a file and “staged” it, i.e. told Git that you’re getting ready to save a new version of the file. This is the _staged area_. Before staging a file, however, you must enter it into your working directory so that Git becomes aware of the file you are working with. _See figure 1.2._







![Figure 1.3](images/git_init.png "Figure 1.3")








Git gives you several options besides simply tracking, staging, and committing files.

######_Ignore files in your repository_
You might have files saved in your repository that you do not want Git to track (i.e. keep showing up when you type “git status”). This requires creating a “hidden” file first. Programs on your computer automatically create files that store data. These files are not intended for the user to open, and therefore remain hidden when the user views files in Finder. 

1. **nano .gitignore**
2. **type** the name(s) of the file(s) Git will ignore (accuracy matters!)
3. **save** changes and **exit** nano
4. **git status** will tell you that you have one untracked file: .gitignore
5. **git add .gitignore**
6.  **git commit -m "[message]"**

Now, when you type git status, you should see only the file(s) that Git is tracking. To modify .gitignore, simply open it in the text editor and add/delete file names, then add and commit those changes to Git.

######_View staged versus unstaged changes_

Let’s say you’ve modified a project then staged the changes in Git. Then, you get sidetracked and take a phone call, grab some coffee, then come back to your work station and continue modifying your project. YOu When you type git status, you’ll see something like this:

![Figure 1.5](images/unstaged_staged.png "Figure 1.5")

This informs you that you’ve made changes to the project since last staging it. To see exactly what changes you made since it was last staged, type

**git diff**

Git will show you the changes that were made since the last stage. Minus signs (-) indicate what was deleted, while plus signs (+) indicate what was added. _See figure 1.6_

![Figure 1.6](images/git_diff.png "Figure 1.6")

While you likely won’t need git diff for tracking a single project, it does help when you’re working on multiple projects at the same time. In this scenario, Git will show you which files have been staged for commit, and which have been modified but not yet staged. More on this in the next section.
**git diff --staged**

*If you modify a project after staging it, you’ll need to stage it again before committing, otherwise you’ll lose the any changes that were saved to it since the earlier stage. 

######_Unstage a file after you've already staged it_

Perhaps you’ve staged the file before realizing there is something else you wanted to modify; or, you’re working with multiple files and you staged them at the same time, but realized you need to unstage one:

**git reset HEAD [file name]**

######_Remove a file that you mistakenly told Git to track, while keeping it on your hard drive_

Maybe you overlooked this file when running the ignore command, and now need to unstage and remove from working directory: 

**git rm –cached [file name]**

######_Remove a file from your working directory AND your hard drive_

* **rm [file name]**
* **git status**
* **git rm [file name]**
* **git commit –a**

######_Changing your last commit_

It’s easy to fix mistakes made when committing a version. Maybe you committed a version before adding a required section, or maybe you messed up the commit message:

**git commit –amend**

Your previous commit message will open in the text editor. If you edit the message, the previous commit message will be overwritten.  

######_Reverting to an earlier version_

At some point in your work flow, you might decide that you don’t like the changes you’ve made since the last commit and want to revert to the previous version of your project. To do this, begin with git status, then

**git checkout -- [file]**


#####Viewing Previous Versions

After you’ve modified and saved several versions of your project, you may decide that you want to view a history of all the commits you’ve made. To do this, type

**git log**

As you can see in the figure below, Git generates a list of all of the commits you’ve done in reverse chronological order. For the Response.rtf example, there were four versions committed to the repository. Perhaps your project has eight versions thus far, but you only see the first four. Terminal only shows you one page of commits at a time. To view the next page of commits, press **space**. To return to the command line, type the letter **q**.

![Figure 1.7](images/git_log.png "Figure 1.7")

######What do you want to know about the previous versions?

There are several commands that allow you to obtain different kinds of information when viewing the commit history. 

######_Viewing differences between versions_

You've already learned **git diff**, the command used to see what changes have been made to the project since its last commit. If you'd like to see the differences between each commit, type

**git log -p**

This command will show you line-by-line differences, which is more helpful for people writing code. If you're working on a presentation, dissertation, or some other lengthy text project, you'll want to use a slightly different command:

**git log -p --word-diff**

As suggested by the command, this will show you the word differences between versions.

######_Limiting the output_

Suppose you have committed many versions of your project and you don't want to see all of them. Following "git log," add the number of commits you want to see with a dash preceding the number:

**git log -3**

This command can be combined with other commands you are making, for instance:

**git log -p --word-diff -3**

######_Make it pretty_

Tired of trying to make sense of the lengthy outputs for each commit? Use the following command to condense the information you need to know into one line for each commit:

**git log --pretty=oneline**

There are plenty of other commands for obtaining the exact information you want to know about each commit, but those listed above are the most common commands a single user may need. If you're tracking a complex project in Git over a long period of time, you might benefit from some of those other commands, which you can find on [Git's website](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History).