##The Git Guide for Mac Users
_Easy-to-follow instructions for using the version control system_

**by Julie Bickford**

---

###Introduction

#####What is Git?

Git is an application that allows you to track a projects's development over time. With Git, you can view earlier versions of the project, view changes made along the way, and revert to a previous version. It also allows multiple authors collaborating on a single project to contribute independently of one another, then merge those several versions again for a final product.
 Git works with virtually any file type; however, it works best with text files. If you need to insert images, create tables, or design a layout, Git cannot specify the exact changes among versions. It can still keep a log of a project's development over time, though.
#####Who can use Git?

Whether you're writing software, designing a website, writing a novel, developing a curriculum, working alone or in a large group, Git helps keep a project organized. You don't need an extensive technical background in order to understand it. Many people who must cooperate with developers, such as graphic designers, quality assurance testers, and IT support staff, may benefit from using Git as it can facilitate communication and collaboration among teams as well. 
#####Where to Find Git
The program is available on [Git’s website](http://git-scm.com/downloads). Follow Git's instructions for downloading and installing the program on your Mac computer.
***
####Before Starting a Project
#####Get Familiar with Terminal
You must be comfortable using Terminal since it serves as Git's user interface. Terminal is located in the Utilities folder, inside the Applications folder. A faster way to access Terminal is to use Spotlight, your computer’s search tool. _See figure 1.1._
<br><br>
![Figure 1.1](images/spotlight.png "Figure 1.1")
<br><br>
Below is a key for common commands and shortcuts used in Terminal.
* **pwd** = _present working directory_
* **ls** = _list contents in the directory_
* **cd** = _change the working directory_
* **control-c** = _cancel previous command_ (maybe you misspelled a word so the command didn't work)
* **up arrow** = _enter previous command_ (continue clicking the up arrow until the desired command is displayed)

Use Terminal, rather than Finder, to manage folders and files:

* **mkdir [foldername]** = _create new folder_ (make sure the present working directory is where you want to store the folder)
* **touch [filename]** = _create new file_ (make sure the present working directory is where you want to store the file; include extension in file name)

* **rm [filename]** = _delete file_ (this command permanently deletes the file form your hard drive, so be careful using it)
Note: Throughout this tutorial, all commands are typed in **bold**. Several commands require you to enter your own information, such as the name of a folder or file, as shown above. _Brackets_ ( [ ] ) are used to indicate information that will be selected by the user. DO NOT include brackets in the command.

		*Helpful tip:
		
		When typing the names of existing files and folders, use this shortcut: 
		"first letter, Tab". Terminal will automatically complete the file name for you.		e.g. "G, Tab" --> "GitDocs"		
#####Configure Settings in GitAfter installing Git, customize your settings for username, email, and text editor. There are many settings you can configure, but those can be addressed once you become more acquainted with the program. 
1. Username
   	**git config --global user.name [John Doe]**

2. Email address:

   	**git config --global user.email [jdoe@somewhere.com]**
	
3. Text editor:

	**git config --global core.editor [name]**
	
	*Please note that nano is the text editor of choice for this tutorial.
	
To check that you  have correctly entered your settings, use the command **git config –list**.  
#####Create a Working Directory

You will need to create a working directory, or a folder that will house the documents related to the project you will track in Git. Store this folder within your home folder for more direct access when working in Terminal.

	Tips for Naming Files:
		* Limit the name to one or two words 
		* Omit spaces in between words if possible
		* Commands in Terminal are case sensitive, so use lower-case names for efficiency
***
 ####Start a New Project as a Single Contributor#####Initializing a Repository
Start by telling Git where to set up a "repository," or a location where it will store all of the information related to each version of the project.  This must be the same folder you are using as your working directory.
In Terminal, change the present working directory to your desired working directory:
**cd [foldername]**
Once you have directed Git to the proper folder, initialize a repository with the following command:
**git init**
    _See figure 1.2._

![Figure 1.2](images/git_init.png "Figure 1.2")
*You can check that you have correctly set up the repository by asking Terminal for the _present working directory_ (pwd).

#####Staging Files

The first step to tracking a file is making Git aware of it. This step is called "staging". "Within your working directory, you may have several files that you want to track (as well as others that you do not want to track--more on this in a bit). Though Git can track many files concurrently, it might be easier to work with only one file as you are first learning the program.
To stage the file that you want Git to track, type**git add [file name]**
If this is an empty file, you may want to make changes to it before saving the initial version in Git. If work is already in progress, you may want to save the initial version sooner than later.
***
####Checking the Status of a File

Before saving a version of your project, check the _status_ of the file by typing **git status**. Status will inform you of several things, including:

1. If changes were made and staged for commit
2. If there are untracked files in the directory
3. If changes were made that have not been staged for commit

Paying attention to the git status output can help you determine what to do next.
#####Changes Were Made and Staged for CommitIf the desired changes have been made and staged, you can then "commit" a version to the repository. This means that Git takes a snapshot of the file at that exact moment and stores that information. Every commit requires a _message_, or reason, for the commit. This message should offer a brief description of its current state, or the milestone you have reached, and you can word it however you like. For example, “initial commit,” “added introduction,” "rough draft"and so on.**git commit –m "[message]"**		
 _See figure 1.3._
<br><br>
  ![Figure 1.3](images/stage_status_commit.png "Figure 1.3") 
<br><br>


#####There are Untracked Files in the Directory
If you have untracked files in your directory that you wish to remain untracked, tell Git to "ignore" them. For example, Figure 1.3 shows two files in the working directory, one tracked (Response.rtf) and one untracked (Git Guide.docx). Git will continue to list Git Guide.docx unless directed otherwise, and this could become distracting when you're working on this project for a long period of time.

In order to ignore a file, you must first create a “hidden” file. Programs on your computer automatically create files that store data. These files are not intended for the user to open, and therefore remain hidden when the user views files in Finder. Follow the series of commands below to create a file type which Git will ignore, stage the file, and commit to the repository:

1. **nano .gitignore** to create a file in which you list the files you want Git to ignore
2. type **[filename(s)]** Git will ignore (accuracy matters!)
3. save changes and exit nano
4. **git status** will tell you that you have one untracked file: .gitignore
5. **git add .gitignore**
6.  **git commit -m "[message]"**

Now, when you type git status, you should see only the file(s) that Git is tracking. To modify .gitignore, simply open it in the text editor and add/delete file names, then add and commit those changes to Git.

#####Changes Were Made but Not Yet Staged

Perhaps you are working on a report for an entire work day, but you don't necessarily want to commit a new version with every paragraph or page you add. This could become tedious, interrupt your work flow, and possibly result in an overwhelming number of file versions. Instead, you stage the file at various times during the day without committing--before lunch, again before the afternoon meeting, then one last time at the end of the day when you finally make a commit.

If you change a file after staging it, a git status command will bring this to your attention. (_See Figure 1.4._) You will need to stage the file again before committing; otherwise, you’ll lose any changes that were made to it since the previous staging. 

![Figure 1.4](images/unstaged_staged.png "Figure 1.4")

######Viewing Differences with git diff

To know that there are staged and unstaged changes is helpful, but it would be better if you could see exactly what was added and/or deleted since you last staged the file. Use **git diff** to see those differences. Minus signs (-) indicate what was deleted, while plus signs (+) indicate what was added. 

Figure 1.5 indicates that the line, "Here are more changes that I haven't staged yet," was deleted from the Response.rtf since its last stage, while nothing new was added. If you want to keep the changes that have been made since the last stage, then stage the file again. If you want to "reset," or unstage the changes that you have made since, then a git status command will show you how to do that.

![Figure 1.5](images/git_diff.png "Figure 1.5")
Similarly, if you want to view the differences between the staged version of a project and its _previous commit_, type
**git diff --staged**

***

####Accessing Information about the Project's Development

#####View the Commit History

After you’ve modified and saved several versions of your project, you may need to view a history of all the commits you’ve made. To do this, type

**git log**

As you can see in the figure below, Git generates a list of all of the commits you’ve made in reverse chronological order. For the Response.rtf example, there were four versions committed to the repository. Perhaps your project has eight versions thus far, but you only see the first four. Terminal only shows you one page of commits at a time. To view the next page of commits, press **space**. To return to the command line, type the letter **q**.
<br><br>
![Figure 1.7](images/git_log.png "Figure 1.7")
<br><br>

#####View Differences between Committed Versions

You've already learned git diff, the command used to see what changes have been made to the project since its last commit. If you'd like to see the differences between each commit, type

**git log -p**

This command will show you line-by-line differences, but only for text files.

#####Limit the Output

Suppose you have committed many versions of a project you have been working on for a month and you don't want to see all of the commits you have made. Following "git log," add the number of commits you want to see with a dash preceding the number:

**git log -3**

#####Make it Pretty

Tired of trying to make sense of the lengthy outputs for each commit? Use the following command to condense the information you need to know into one line for each commit:

**git log --pretty=oneline**

These represent just a few ways in which you can customize the git log output. There are many more, which you can access on [Git's website](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History).

***
####Correcting Mistakes as a Single Contributor

#####Unstage a File after You've Already Staged It

Perhaps you’ve staged a file before realizing there is something else you wanted to modify; or, you’re working with multiple files and you staged them at the same time, but realized you need to unstage one:

**git reset HEAD [file name]**

#####Remove a File from Your Working Directory _While Keeping it on Your Hard Drive_

Maybe you overlooked this file when running the ignore command, and now need to unstage and remove from working directory: 

**git rm –cached [file name]**

#####Change Your Last Commit

It’s easy to fix mistakes made when committing a version. Maybe you committed a version before adding a required section, or maybe you messed up the commit message:

**git commit –amend**

Your previous commit message will open in the text editor. If you edit the message, the previous commit message will be overwritten.  

#####Revert to the Previous Version

At some point in your work flow, you might decide that you don’t like the changes you’ve made since the last commit and want to revert to the previous version of your project. To do this, begin with git status, then

**git checkout -- [file]**

<br><br>

		*Helpful Tip:
		For a reference list of Git commands, type **git help** at any time.



---
<br><br>
These commands should be enough to start tracking a file in Git as a single contributor. If you'd like to learn more advanced features Git offers, such as collaboration among several authors, the next section will be available soon!