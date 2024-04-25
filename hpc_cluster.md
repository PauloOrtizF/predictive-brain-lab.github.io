# The HPC DCCN Cluster and Linux

This wiki page is here to try to provide some concise but useful information on how to navigate the HPC DCCN cluster. It makes use of the existing resources at the DCCN (by providing links to them) in addition to experiences from lab members and workshops given by the TG. In contrast with the HPC DCCN Wiki, this document should be more digestible and accessible to researchers with different backgrounds. 

Nonetheless, we will list resources that will be helpful when trying to work with the cluster:
-	[HPC Cluster Wiki](http://hpc.dccn.nl/) – this contains all the relevant information, according to the TG, that you will need to use the cluster.
-	[Intranet HPC](https://intranet.donders.ru.nl/index.php?id=hpc) – this contains information relevant to the HPC at the DCCN
-	[Recordings of the HPC Tutorials Given by the TG](https://hpc.dccn.nl/docs/tutorials/index.html) – if you do not feel confident in doing things by simply reading documents. The TG organizes every six months interactive tutorials on how to use the cluster. If you do not want to wait, the link provided has some recordings from previous years. Note: to access the link you need to be on a DCCN network.  Also, the information there might be outdated.

Most of the time, scientific computations require the usage of a lot of data and computer power. A major goal for any scientist is to be able to carry out these processes as fast as possible. The way this can be achieved is by parallel computations, using multiple computers at the same time to work on your data. The DCCN has a High-Performance Cluster (HPC) which allows any employee to do exactly this. This wiki page is dedicated to providing you with information about the cluster and how to use it effectively. 

_NOTE_: The DCCN is transitioning on the software used for the cluster, so this page will contain information on both the current way of using it and the future software manager. 

The system that connects multiple computers together is what we call **the cluster**. Importantly, the operating system that is used to connect these computers is [LINUX](https://en.wikipedia.org/wiki/Linux). Hence, to make use of this high-performance computer you will have to become familiarized with it. 

- [Cluster Access](#cluster-access)
  - [Command Line Access (CLI)](#command-line-access-(cli))
  - [Virtual Network Computing (VNC)](#virtual-network-computing-(vnc))
- [Linux and Bash (Shell) Basics](#linux-and-bash-(shell)-basics)
  - [Linux](#linux)
  - [Bash and Zsh (Shell)](#bash-and-zsh-(shell))

## Cluster Access

You can access the cluster both on any computer in the DCCN building or through your personal laptop. The important thing to remember is to be connected to the DCCN network through your eduVPN account (if you need help to do this, you can [contact the TG](https://intranet.donders.ru.nl/index.php?id=helpdesk)).

When you are connecting to the cluster, you are not directly accessing the high-performance computers. Instead, you access what is called **access nodes** that allow you to “talk” to the HPC and send in your work. These access nodes can be thought of as external computers that you can access through your laptop (when you perform things in these access nodes, the computer power comes from them and not your laptop. Your laptop becomes some sort of “screen” for them). These **access nodes** are called **mentat001, mentat002, mentat003, mentat004, mentat005, mentat006.**

**Important**: 
-	The access nodes are NOT a computer cluster, but they are linked to it. 
-	You are NOT allowed to run heavy computations on them. 
-	They have very limited memory/RAM (only 4gb)

There are two ways of accessing one of the cluster nodes: a **command line interface (CLI)** and a **graphical user interface (GUI)**. From the CLI you will use a terminal to navigate the access nodes and communicate with the HPC. From the GUI you will see a graphic LINUX desktop window on your computer which you can navigate and use the terminal there to send your commands. 

### Command Line Access (CLI)
The command line access allows you to connect with one of the access nodes using a terminal interface (i.e., you will be using the **access node** computer only by typing in LINUX commands in the terminal).  From there you can access all of your user data present in the DCCN cluster as well as send your analyses to the HPC. To effectively use the terminal, you will have to learn how to navigate it using certain commands. If you are not familiar with this, check here for resources to learn how to do it .[INSERT LINK TO LINUX BELOW]

#### How to Connect to the CLI?

For **Windows users** see the instructions [here](https://hpc.dccn.nl/docs/cluster_howto/access-internal.html#ssh-login-with-putty).
_Tips and Tricks_
-	You can use any of the mentat00x servers. Connect to anyone you want. 
-	The configuration on the WIKI is exactly how the screen in your computer should look like 
-	When you are logging in with your username and password, you will not see the password being typed. However, it is there, so once you finish simply click enter (this is the same username composed of the three first letters of your name and surname)

For **MacBook users**
The wiki does not contain information on how to do it. For this software, you will not be making use of PUTTY. 
These are the steps:
-	Open the terminal of your computer (`cmd+spacebar` and type in `terminal`)
-	In the terminal you will directly type:
`ssh username@mentat001@.dccn.nl` (e.g., ssh pauort@mentat001.dccn.nl)


-	You will be prompted to insert your password (your typing will not be appearing, but it is being typed).
-	Done! You will see a message that says you have effectively connected to the server on your terminal. 

### Virtual Network Computing (VNC)
The VNC allows you to connect with one of the **access nodes** using a graphical user interface (GUI). This means you will see a new desktop window that allows you to use the access node as if it were your own desktop (e.g., run apps, open folders, etc.). Within that LINUX desktop, you can open a terminal and use it to communicate with the HPC. 

The general two stages to set up the VNC are the following:
1.	Start the VNCserver (in the remote system (i.e., access node))
2.	Use a VNCviewer client (personal desktop) to connect (to remote) VNCserver

The step-by-step to connect to the VNC for both Windows and MacBook users are essentially identical. You can find the detailed steps with illustrations on this [page](https://hpc.dccn.nl/docs/cluster_howto/access-internal.html#vnc-for-graphic-desktop). 

_Tips and Tricks_
-	The first time you start a VNC server, it will prompt you to enter a password. This is a new password unique for when you use the VNC (not related to any of your other accounts). This is done so other users are unable to join your session. 
-	In step 2, when you select a host. Go for the first option as usually, this is the recommendation from the system.
-	Remember to always write down the VNC server associated with a display endpoint – `mentat00x.dccn.nl:xx` (you want to keep track of the numbers in the spaces occupied by the x’s here). This is so you can tell your computer to which serve to connect once you set up the GUI.  
-	For MacBook users, you will need to download the Tiger VNC Viewer. You can do that [here](https://tigervnc.org/). Click on the GitHub release page, then on the sourceforge website and download the latest version. 

## Linux and Bash (Shell) Basics
Before describing how to use the HPC cluster it is important that you become familiar with using Linux and Bash commands, as this is the language you will be using to send in your work.  If you are familiar with this, feel free to skip it and go to the section: Using the HPC Cluster. [INSERT LINK HERE WHEN IT IS READY]

_Note_: if you are working from the terminal of a MacBook, this will not be using bash but a similar language called **zsh** (Z shell). Look online at the differences between both. You can still use bash if you use the terminal on the VNC GUI or by changing the language on your Macbook from zsh to bash if you prefer it. 

A very fun, easy-to-understand and useful resource to learn Linux, CLI and Bash is this series of [comics by Julia Evans](https://wizardzines.com/comics/). It usually simplifies concepts and help us understand what we are doing when using these tools. 

Additionally, a resource to learn shell or lab skills for research computing is [Software Carpentry](https://software-carpentry.org/lessons/). 
“Cheat Sheet for Linux” [here](https://hpc.dccn.nl/docs/linux/practice/filesystem.html). 
“Bash Cheat Sheet” [here](https://hpc.dccn.nl/docs/bash/cheatsheet.html#cheat-sheet).

### Linux
The HPC Wiki website contains very useful information on Linux basics, providing explanations for the different commands as well as code examples. You can see those [here](https://hpc.dccn.nl/docs/linux/practice/filesystem.html).

If you want to get some hands-on practice with Linux systems before using them in your work. The HPC wiki also contains a series of tutorials to get you familiar with the environment. You can see those [here](https://hpc.dccn.nl/docs/linux/practice/exercise_fs.html). 

### Bash and Zsh (Shell)
It is not very simple to describe what bash is. However, understanding it thoroughly is not fundamental to be able to use it. In simple terms, bash or zsh are programming languages tightly integrated within the operating system. Bash is both a **command-line interface (CLI)** and a **scripting language**, allowing such repetitive tasks to be done automatically and quickly. With the proper commands, it can repeat tasks with or without some modification as many times as we want.



