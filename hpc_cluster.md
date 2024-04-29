# The HPC DCCN Cluster and Linux

This wiki page is here to try to provide some concise but useful information on how to navigate the HPC DCCN cluster. It makes use of the existing resources at the DCCN (by providing links to them) in addition to experiences from lab members and workshops given by the TG. In contrast with the HPC DCCN Wiki, this document should be more digestible and accessible to researchers with different backgrounds. 

Nonetheless, we will list resources that will be helpful when trying to work with the cluster:
-	[HPC Cluster Wiki](http://hpc.dccn.nl/) – this contains all the relevant information, according to the TG, that you will need to use the cluster.
-	[Intranet HPC](https://intranet.donders.ru.nl/index.php?id=hpc) – this contains information relevant to the HPC at the DCCN
-	[Recordings of the HPC Tutorials Given by the TG](https://hpc.dccn.nl/docs/tutorials/index.html) – if you do not feel confident in doing things by simply reading documents. The TG organizes every six months interactive tutorials on how to use the cluster. If you do not want to wait, the link provided contains recordings from previous years. _Note_: to access the link you need to be on a DCCN network. Also, some of the information there might be outdated.

Most of the time, scientific computations require the usage of a lot of data and computing power. A major goal for any scientist is to be able to carry out these processes as fast as possible. A way this can be achieved is through parallel computations: using multiple computers at the same time to work on your data. The DCCN has a High-Performance Cluster (HPC) which allows researchers to do exactly this. **This wiki page is dedicated to providing you with information about the cluster and how to use it effectively.** 

_NOTE_: The DCCN is transitioning on the software used for the cluster, so this page will contain information on both the current way of using it (Torque) and the future software manager (SLURM). 

**Table of Contents**

- [Cluster Access](#cluster-access)
  - [Command Line Access (CLI)](#command-line-access-cli)
  - [Virtual Network Computing (VNC)](#virtual-network-computing-vnc)
- [Linux and Bash (Shell) Basics](#linux-and-bash-shell-basics)
  - [Linux](#linux)
  - [Bash and Zsh (Shell)](#bash-and-zsh-shell)
    - [What is Bash Scripting?](#what-is-bash-scripting)
    - [Transferring Files](#transferring-files)
- [Using the Cluster](#using-the-cluster)
  - [Job Submission](#job-submission)
  - [Job Resource Requirements](#job-resource-requirements)
- [Data Analysis Software](#data-analysis-software)
  - [Using Integrated Development Environments on the Cluster](#using-integrated-development-environments-on-the-cluster)
- [Data Analysis in Parallel](#data-analysis-in-parallel)
- [Contact](#contact)

## Cluster Access

The system that connects multiple computers together is what we call **the cluster**. You can access it using any computer in the DCCN building or through your personal laptop. The important thing to remember is to be connected to the DCCN network through your eduVPN account (if you need help to do this, you can [contact the TG](https://intranet.donders.ru.nl/index.php?id=helpdesk)).

When you are connecting to the cluster, you are not directly accessing the high-performance computers. Instead, you access what is called **access nodes** that allow you to “talk” to the HPC and send in your work. These **access nodes** are called **mentat001, mentat002, mentat003, mentat004, mentat005, mentat006.**

**Important**: 
-	The access nodes are NOT a computer cluster, but they are linked to it. 
-	You are NOT allowed to run heavy computations on them. 
-	They have very limited memory/RAM (only 4gb)

There are two ways of accessing one of the access nodes: a **command line interface (CLI)** and a **graphical user interface (GUI)**. From the CLI you will use a terminal (shell) to navigate the access nodes and communicate with the HPC. From the GUI you will see a graphic desktop window (running on [LINUX](https://en.wikipedia.org/wiki/Linux) software) on your computer which you can navigate and use the terminal there to send your commands. 

### Command Line Access (CLI)
The command line access allows you to connect with one of the access nodes using a terminal interface (i.e., you will be using the **access node** computer only by typing in commands in the terminal).  From there you can access all of your user data present in the DCCN cluster as well as send your analysis to the HPC. 

To effectively use the terminal, you will have to learn how to navigate it using certain commands (using LINUX). If you are not familiar with this, check [here](#linux) for resources to learn how to do it.

#### How to Connect to the CLI?

For **Windows users** see the instructions [here](https://hpc.dccn.nl/docs/cluster_howto/access-internal.html#ssh-login-with-putty).

_Tips and Tricks_
-	You can use any of the `mentat00x` servers. You can connect to whichever you want. 
-	The configuration on the HPC WIKI is exactly how the screen in your computer should look like 
-	When you are logging in with your username and password, you will not see the password being typed. However, it is there, so once you finish, simply click enter (this is the DCCN account in which the username is composed of the three first letters of your name and surname)

For **MacBook users**

The HPC wiki does not contain information on how to do it. For this operating system (OS), you will **not** be making use of PUTTY. 

These are the steps:
-	Open the terminal of your computer (`cmd+spacebar` and type in `terminal`)
-	In the terminal you will directly type:
`ssh username@mentat00x@.dccn.nl` (e.g., ssh pauort@mentat003.dccn.nl)
-	You will be prompted to insert your password (your typing will not be appearing, but it is being typed).
-	Done! You will see a message that says you have effectively connected to the server on your terminal. 

### Virtual Network Computing (VNC)
The VNC allows you to connect with one of the **access nodes** using a graphical user interface (GUI). This means you will see a desktop window pop-up that allows you to use the access node as if it were your own desktop (e.g., run apps, open folders, etc.). Within that LINUX desktop, you can open a terminal and use it to communicate with the HPC. 

The general two stages to set up the VNC are the following:
1.	Start the VNCserver (in the remote system (_i.e.,_ access node))
2.	Use a VNCviewer client (on your personal desktop) to connect (to a remote) VNCserver

The step-by-step to connect to the VNC for both Windows and MacBook users are essentially identical. You can find the detailed steps with illustrations on this [page](https://hpc.dccn.nl/docs/cluster_howto/access-internal.html#vnc-for-graphic-desktop). 

_Tips and Tricks_
-	The first time you start a VNC server, it will prompt you to enter a password. This is a **new password unique for when you use the VNC** (not related to any of your other DCCN accounts). This password is needed so other users don't join your session. 
-	In step 2, when you select a host. Go for the first option as this is the recommendation given by the system.
-	Remember to always write down the VNC server associated with a display endpoint – `mentat00x.dccn.nl:xx` (you want to keep track of the numbers in the spaces occupied by the x’s here). This is so you can tell your computer to which serve to connect once you set up the GUI.  
-	For MacBook users, you will need to download the Tiger VNC Viewer. You can do that [here](https://tigervnc.org/). Click on the GitHub release page, then on the sourceforge website and download the latest version. 

## Linux and Bash (Shell) Basics
Before describing how to use the HPC cluster it is important that you become familiar with Linux and Bash commands, as this is the language you will be using to send in your work.  If you are familiar with both of them, feel free to skip it and go to the section: [Using the HPC Cluster](#using-the-cluster).

_Note_: if you are working from a MacBook terminal, the default language will not be bash but a similar language called **zsh** (Z shell). Look online at the differences between both. You can still use bash if you use the terminal on the VNC GUI or by changing the language on your Macbook from zsh to bash. 

A very fun, easy-to-understand and useful resource to learn Linux, CLI and Bash is this series of [comics by Julia Evans](https://wizardzines.com/comics/). It simplifies concepts and helps understand how to use these tools. 

Additionally, a resource to learn shell or lab skills for research computing is [Software Carpentry](https://software-carpentry.org/lessons/).

These two links provide some concise cheat sheets for Linux and Bash:
- “Cheat Sheet for Linux” [here](https://hpc.dccn.nl/docs/linux/practice/filesystem.html). 
- “Bash Cheat Sheet” [here](https://hpc.dccn.nl/docs/bash/cheatsheet.html#cheat-sheet).

### Linux
The HPC Wiki website contains very useful information on Linux basics, providing explanations for the different commands as well as code examples. You can see those [here](https://hpc.dccn.nl/docs/linux/practice/filesystem.html).

If you want to get some hands-on practice with Linux systems before using them in your work. The HPC wiki also contains a series of tutorials to get you familiar with the environment. You can see those [here](https://hpc.dccn.nl/docs/linux/practice/exercise_fs.html). 

### Bash and Zsh (Shell)
It is not very simple to describe what bash is. However, understanding it thoroughly is not fundamental to be able to use it. In simple terms, bash or zsh are programming languages tightly integrated within the operating system (OS). Bash is both a **command-line interface (CLI)** and a **scripting language**, allowing repetitive tasks to be done automatically and quickly. With the proper commands, it can repeat tasks with or without some modification as many times as we want.

![Shell](/images/shell_illustration.png)

Your computer is usually organized in the manner shown in the figure above. Most of the time, users interact with applications (_e.g.,_ MATLAB) that directly connects them to the kernel and hardware without having to directly specify what to do (_ie.,_ you interact with the GUI of the app). **By using bash or zsh, you tell the kernel directly how you want your data to be processed**. While a GUI presents you with choices to select, CLI choices are not automatically presented to you – **we must learn commands!**

Familiarity with the shell (bash or zsh) is near essential to run a variety of specialized tools and resources including high-performance computing (HPC) systems. Thus, being able to interact with the shell is becoming a necessary skill for (data) science. 

![What_Shell](/images/what_is_shell.png)

In very simple terms: bash says _“Give me input from the terminal, I will process that input, tell the kernel what to do, and send output somewhere for you”._

For our specific case as members of the lab, we will give bash commands to run our (MATLAB or Python) scripts and the output will be saved somewhere (specified by us) in our files. 

The [following page](https://hpc.dccn.nl/docs/bash/start.html) from the HPC Wiki contains an introduction, example code, and tutorials on how to use BASH scripting language. 

These are a series of tips to keep in mind to get working commands:

-	Bash treats spaces, tabs, and new lines as white spaces. In this scripting language, a white space separates _words_ in bash. The first word is always a command and the following arguments. For instance: `ls -a /path/to/my/favorite/file*txt`. In this case `ls`(command) [space] `-a`(option) [space] `/path/to/my/favorite/file*txt` (operand)

-	Variables are assigned as `variable=value`. Without any spaces. 
To call for a variable, you must use `$variable`. 

-	Anything in quotes will be processed as a single word, including spaces. Single quotes remove special meaning from characters inside of them (_i.e.,_ everything between single quotes will be processed as a literal character). Double quotes only escape spaces and single quotes. 

-	Bash is case sensitive. So be careful for any typos!

-	Always check that you are specifying the correct directories for running scripts, using programs, saving output, etc. 

#### What is Bash Scripting?
Instead of directly typing bash commands to your terminal, you can make use of scripts that include commands to do so. You simply open a text editor and write your commands in there! (either by opening the text editor in the terminal or by using your VNC GUI). See [here](https://hpc.dccn.nl/docs/bash/start.html) for more info on how to use the text editor on the terminal. 

The reason why you would use this is to reduce errors, create analysis pipelines, work faster, etc. Overall, it automatizes processes and makes your work reproducible for you and other researchers. 

To use it you simply set the document as executable ` $ chmod +x myscript.sh ` and run it by simply typing its name on the terminal and hitting enter ` $ /path/to/my/file/myscript.sh ` 

_Note:_ For the system to read a text file as a bash command, you need to start it with `#!/bin/bash ` and use the file extension **.sh**


_For Loops and If statements in Bash_

Some of you might be familiar with **For Loops** and **If statements** from other programming languages. In Bash Scripts you can also make use of these functions. 

The reason why these are helpful is because you can make use of them to run multiple scripts, functions, etc. without having to add many lines to them or execute multiple scripts. They also reduce the amount of typing and can avoid small mistakes. 

In bash you can for every item on a list execute a list of commands (this is very useful to remember!)

![for_loop_bash](/images/for_loops_bash.png)

You can look online on how to use for loops, but this illustration should give you a good idea! 

If statements are typically employed in parallel with for loops and help to stop a loop from running once a condition has been met. 

![if_stat_bash](/images/if_stat_bash.png)

Here, we provide a small example of an if statement and useful test operators. For more information, search on the internet. Software carpentry has a series of lessons on how to use shell for scientific computations [here](https://swcarpentry.github.io/shell-novice/).

#### Transferring Files
To copy large data files between your home computer and the cluster you can use [RSync](https://rsync.samba.org/). It offers a variety of options to control the way you share your information. You can do it very easily using the shell:

```rsync -av sourcefile youruser@localhost:target address```

_We still recommend checking the website to understand better how to do these transfers._ Try to never copy-paste code that you do not understand fully.

Alternative options for RSync are:
-	[RClone](https://rclone.org/) (Similar to RSync but for cloud-based storage)
-	[SCP](https://www.ssh.com/academy/ssh/scp) (Secure Copy)
-	GitHub (Useful to already store scripts and documents for later reference and publication. You can setup [SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) and easily have remote folders on the server and your personal laptop.)

## Using the Cluster
The compute nodes at the HPC are currently managed by the Torque resource manager. Instead of allowing users to log in to one high-performance computer and run computations freely, user **submit** their computations in the forms of **jobs** to the Torque cluster. Here, the Torque will create a schedule and submit the work according to a series of considerations (you will have to set resource requirements and based on this the jobs will be arranged in job queues). Practically, having the Torque resource manager means that certain commands, specific to Torque, in your CLI or the terminal of the VNC GUI will allow you to submit jobs.

**Important Information.
The DCCN is changing from Torque manager to SLURM. This means the commands to connect to the cluster will be shortly changing. If you are new and wish to only learn SLURM you can see the HPC WIKI page for it [here](https://hpc.dccn.nl/docs/cluster_howto/compute_slurm.html). We do not recommend only using SLURM as it is still in the testing phase. Why is the change happening? Slurm is open source, allows for better error handling and is the new leader in HPC computing.** 

To get more information on the [job prioritization](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#resource-sharing-and-job-prioritisation) and [job resource management flow](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#job-management-workflow), you can see the highlighted pages on the HPC Wiki.


There are three key functions for the job management workflow:
1.	`$ qsub ` - this is to submit a job to the cluster 
2.	` $ qstat ` - this is to monitor the job status on the cluster
3.	 `$ qdel ` - this is to delete a job from the cluster

To check for the output files after your job has run, you can use:
-	` $PWD/STDIN.o<JOBID>` - to see the output
-	` $PWD/STDIN.e<JOBID> ` - to see any errors

### Job Submission

There are two main ways in which you can send job submissions to the cluster: **batch submissions and interactive submissions.** 
The main difference is that in **batch submissions** you simply tell the cluster what to do and you can go on with your life until it is done. Using **interactive submissions** means that you can either use the CLI and run your commands directly on the cluster or connect GUIs to the cluster and run software such as MATLAB from there. 
This is a small cheat sheet on job submissions for the cluster:

![job_resource_management](/images/job_submission_management.png)

To get more information on batch submissions you can visit [this page](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#batch-job-submission) on the HPC wiki. If you want to have a more hands-on approach, you can access this [link](https://hpc.dccn.nl/docs/cluster_howto/exercise_simple/exercise.html) with a practical exercise for batch submissions.

Interactive job submissions can take two forms:
1.	**Interactive computation in text mode**
You run a command line in your shell (terminal) and select the interactive option. This will allow you to connect to the HPC cluster and any computation you run in the shell from then onwards will be processed by the cluster.  This can be thought of as connecting the CLI to the HPC. For more information and code examples see [here](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#interactive-computation-in-text-mode). 

2.	**Interactive computation in graphic mode**
Ideally, you would like to run your software such as MATLAB or Python directly using the HPC cluster. In that way, you can do all your regular analyses using a GUI but having the HPC computational resources. This is possible with the interactive computation in graphic mode. The important thing to remember is to be connected to the VNC GUI on your laptop. To see how to do this, open this [page](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#interactive-computation-in-graphic-mode).

In this [page](https://hpc.dccn.nl/docs/cluster_howto/exercise_interactive/exercise.html), you have exercises to practice interactive job submissions. 

[Here](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#checking-job-status), you can see instructions on how to see the status of the jobs you have submitted. 

### Job Resource Requirements
Every job you submit to the cluster will have to come with resource requirements. In this way, the Torque manager can properly allocate the necessary resources for your job. In order to not run into any problems, you need to make sure that there are sufficient resources specified in your submission. 

You can visit this [page](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#specifying-resource-requirement) to get more information on how to specify your resource requirements. 
_Note_: for some analyses, you might have very specific requirements on properties of the HPC cluster you want to access (e.g., you want to use cuda, gpus, etc.). You can specifu these in your resource requirements when submitting a job. The HPC wiki link above contains more information on the different requirements you can select. 

It might be hard to estimate how many resources you require for a specific job. To make accurate estimations you can:
-	Ask other more experienced colleagues 
-	Run tests, check the status of your job
-	Run an interactive job and check VNC which shows graphical statistics-window of the running job (an estimate of the requirements)
-	check the epilogue message at end of the output file `<job_name>.o<jobID>`

For more information, see [here](https://hpc.dccn.nl/docs/cluster_howto/compute_torque.html#estimating-resource-requirement). 
**Important**: try to not overestimate largely the resources you need. In this way, more people can use the cluster simultaneously.  For an exercise on resource requirements, see [here](https://hpc.dccn.nl/docs/cluster_howto/exercise_resource/exercise.html). 

## Data Analysis Software

To run the different options of software in the cluster, a tool called Environment Modules is used. This allows you to see all the different programs installed in the software as well as their different versions. From there, you can load the one you need and use it accordingly. On this [page](https://hpc.dccn.nl/docs/cluster_howto/software-modules.html), you can find more information on how to check the software and load the one you need. If you want to get a more hands-on approach, check [this set of exercises](https://hpc.dccn.nl/docs/cluster_howto/exercise_env_modules/exercise.html). 

Certain applications are widely used and do not require any loading to connect to the cluster. Utility scripts are provided to integrate with job submissions to the Torque cluster. These applications are MATLAB, R and Jupyter Notebooks. For more information on how to use these in this form, see [here](https://hpc.dccn.nl/docs/cluster_howto/software-scripts.html). 

The HPC Wiki also contains more information on how to effectively use MATLAB, R, and Python (in general) on the cluster. These pages are relevant on how to create environments, use specific versions, and understand the features that have been hand-crafted by the TG to make your analysis pipelines as smooth as possible:
-	[MATLAB](https://hpc.dccn.nl/docs/cluster_howto/exercise_matlab/exercise.html)
-	[R](https://hpc.dccn.nl/docs/cluster_howto/exercise_R/index.html)
-	[Python](https://hpc.dccn.nl/docs/cluster_howto/exercise_python/exercise.html)

### Using Integrated Development Environments on the Cluster 
There are two integrated development environments (IDE) that you can use for coding and have specific ways of connecting them to the cluster. For some cases, this means you might be able to run the program from your laptop by using the integrated terminal in the program to connect to the cluster. 
The two options currently available are:
1.	PyCharm – an IDE for Python project. You can find more information about the IDE and how to use it in the cluster [here](https://hpc.dccn.nl/docs/cluster_howto/ide-pycharm.html). 
Our lab member Maartje Koot created a small tutorial on setting up PyCharm Pro to Run Jupyter Notebooks in the cluster. You can find that [here](/cluster/Notebooks_in_PyCharm_on_Cluster_KOOT.pdf). 

2.	VSCode -- is a cross-platform source-code editor made by Microsoft. It is great for laptops that do not have a lot of memory/RAM as it is very light. [This page](https://hpc.dccn.nl/docs/cluster_howto/ide-vscode.html) contains information on connecting your local VSCode to the cluster server.
The developers of VSCode also have official documentation on how to do this [here](https://code.visualstudio.com/docs/remote/tunneling). 

## Data Analysis in Parallel 

This section can be thought of as a tips and tricks for a specific situation: you have collected data from **multiple subjects** and you want to perform an **analysis** on each subject’s data independently. Using some of the resources above, especially knowledge of bash, you can run all these analyses in parallel and avoid running each one of them script-by-script. 

This [section](https://hpc.dccn.nl/docs/cluster_howto/exercise_da/exercise.html#exercise-da) of the HPC cluster WIKI has a small exercise in Python, R and MATLAB to see how you can do this in each of these software options. 

## Contact
If you run into any problems, you can contact the [TG help desk](mailto:mailto:helpdesk@fcdonders.ru.nl). They are always available to help with technical questions. 

Every year, a PhD student takes on the PhD job to help researchers at the DCCN with any cluster problems they might have. Especifically, anything related to running specific software used for neuroimaging analyses on the cluster. The current person responsible for this is Lennart Oblong (Room 02.284), but always double check as these jobs are constantly changing. 
