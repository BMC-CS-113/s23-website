---
layout: default
title: Hello World & Errors
type: Lab
number: 00
active_tab: lab
release_date: 2023-01-16

---

<!-- Check whether the assignment is ready to release -->
{% capture today %}{{'now' | date: '%s'}}{% endcapture %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% if release_date > today %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
<!-- End of check whether the assignment is up to date -->


<!-- Check whether the assignment is up to date -->
<!--{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}-->
<!-- End of check whether the assignment is up to date -->



{% if page.materials %}
<div class="alert alert-info">
You can download the materials for this assignment here:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>

</div>
{% endif %}





{{page.type}} {{page.number}}: {{page.title}}
=============================================================

## Objectives:

The main goals for this lab are:

1. Get familiar with the command line
2. Set up your course directory on the CS machines
3. Start using vim


## 1. CS Lab Machines & The Command Line
The computers in the lab rooms (Park 230 and 231) are dual booted with Windows 10 and Ubuntu (a version of linux). This means that you can use either the Windows or Linux operating systems (OS). For this course, we will be using Linux. 

You should have received an email from David Diaz with your credentials to the Computer Science lab machines. If you did not receive credentials from him, immediately stop by his office in Park 294.

***TODO 1:*** Log into the Linux (Ubuntu) OS using the credentials you received from David. **Note:** These are not your BMC/HC credentials that you normally use.

After logging in, click on the grid on the bottom left of the screen. This will launch a screen showing all the applications. In the search bar on top, type `terminal`, and then click on the application. This will launch the terminal. In this semester we will be working primarily in the terminal.  

### Understanding the Command Line
As soon as the terminal application launches, you should see a black screen. This is where you will type command line commands. For now, we haven't covered any commands in detail so just type anything into the terminal. 


> Note: there is a difference between the terms *terminal*, *command line*, and *shell*, but we will be using them interchangeably. See [GeekForGeeks](https://www.geeksforgeeks.org/difference-between-terminal-console-shell-and-command-line/) if you are curious about the differences.


To run a command in the terminal, click `Enter`. After typing anything into the terminal (here I mean actually mean anything), click `Enter`.

***TODO: Question 1.1:*** After you click `Enter`, what does the terminal tell you?
<br>
<br>
<br>

#### Change your password
You can completely interact with your computer using just the terminal! When a new account is created for you on any computer system, you should always change your password.

***TODO: Change your password!*** In terminal, type the command `psswd` and then press `Enter` and then follow the instructions to change your password.

<details><summary><b style="color:DodgerBlue;">Click me for help if you get stuck</b></summary>

Yes, `psswd` is not a valid command. You should see an error message in the terminal that tells you the correct command. 
</details> 

<br>

#### Command Line Prompt
All of the text thats on the left of where you are typing commands is called the `prompt`. You should notice that there are two words in the prompt that are seperated by an `@` symbol.
For example, my prompt says `apoliak@tsunami:~$`. 

***TODO: Question 1.2:*** What are the two words in your prompt? What does the first word indicate (the word infront of the `@`)? What does the second word indicate (the word after the `@`)?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

To find out what the second word represents, look around the lab computer you are using for an idea.
</details> 

<br>
<br>
<br>

#### Navigation Commands!
Now we are ready to start using command line arguments. We will be using these command lines today:
- ls
- cd
- mkdir 
- wget 
- cat
- wc

##### **`pwd` command**

The first command we'll look at is `pwd`. This command prints the __p__ath to the __w__orking __d__irectory.

Computers are sturctured in a directory hierarchy where directories can contain other directories or files. A directory is just another way of saying a folder.

Run the command `pwd` (this means type `pwd` in the command line and click `Enter` - we'll be moving to this terminology).

***TODO Question 1.3:*** What gets printed out? What do you think it means?

<br>
<br>
<br>

##### **`ls` command**
The next command will look at is `ls`. Instead of us first describing this command, we'll let you try it out yourself. Run the command `ls`.

***TODO: Question 1.4:*** What do you see printed out on in the terminal? What do you think all of that means?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
On your desktop, you likely have a folder with your username. Click on that and compare what opens up with what you see in your terminal.
</details> 

<br>
<br>
<br>

We can add arguments to the `ls` command. After typing in `ls`, type the output of the `pwd` command. For example, I would run the following command:

```
ls /home/apoliak/
```

***TODO: Question 1.5:*** When you run `ls` with the path to your working directory, what do you see? Do you see anything different than before when you ran just `ls`? Why or why not?

<br>
<br>
<br>

##### Piping

We can pass the output from one command as an argument to another command by using the `|` symbol.
Run the following command 

```
pwd | ls
```

***TODO: Question 1.6:*** What do you see? Do you see anything different than before when you ran just `ls`?
Why or why not?

<br>
<br>
<br>

#### Home directory

So far we've used `ls` to look at the files and folders in our ***home*** directory. A home directory is where all the files and folders that belong to a specific user exists. 

***TODO:*** Look carefully again at the command line prompt. At the end of the line after the name of the machine you are working on, you should see two characters. What symbols do you see? One of those represents your home directory - which one do you think it might be?

We can answer this question by using the `ls` command.
***TODO:*** Run the ls command twice, each time add one of the characters/symbols as an argument to ls. For example, if the characters were `A` and `B` (they are not), you would run

```
ls A
ls B
```
The output of running `ls` with each character would give you a hint of which of the two symbols represents your home directory.

***TODO Question 1.7:*** So, which of the two characters/symbols represent your home directory? 

<br>
<br>
<br>

#### Absolute vs Direct Paths

So far we used `ls` to look at files in our own directory. When we run the command `ls /home/<USERNAME>` (here <USERNAME> is a place holder for your actual username), the argument was an **absolute path**. An absolute path is the path from the root (or top) of the computer/file system. We can also specify **relative paths**. These are paths that go from the current working directory to another folder that we specify. For example, when we run `ls Downloads/`, that will tell us what files and folders exist in the Downloads directory.

***TODO Question 1.8:*** If we wanted to see what files exist in the Downloads directory but using an absolute path, what argument would we pass to `ls`?

<br>
<br>
<br>

#### Viewing other directories 

From `pwd`, we see that the path to our home directory was `/home/<USERNAME>`.

***TODO Question 1.9:*** How do you think we could use `ls` to find out what other users have an account on the CS lab machines?

<details><summary><b style="color:DodgerBlue;">HINT 1</b></summary>

We can add a specific absolute path as an argument to the `ls` command

</details>

<details><summary><b style="color:DodgerBlue;">HINT 2</b></summary>

The absolute path to your home directory was `/home/<USERNAME\>/`, so what directory does your home directory live in?

</details> 

<br>


We can also use a relative path. From your own directory, run the following command:

```
ls ../
```

***TODO Question 1.10:*** What do you think that did? What do you think `../` means?

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
That command printed out the contents of the parent directory. `../` represents that parent directory.
</details> 

<br>
<br>
<br>



##### **`cd` command**
The next command will look at is `cd`, which stands for change directory. 

Like `ls`, you can pass an argument to the `cd` command. Here the argument we pass in is the directory we want to move to.

***TODO Question 1.11:*** Run the command `cd Downloads/`.
What changed in the command line prompt? What do you think that tells us?

 <details><summary><b style="color:DodgerBlue;">Hint</b></summary>
Run the `pwd` command.
</details> 

We can also run `cd` without any arguments.

***TODO Question 1.12:*** Run `cd` without any arguments. 
Based on the prompt, what directory do you think we are now in? 

 <details><summary><b style="color:DodgerBlue;">Hint</b></summary>
Run the `pwd` command.
</details> 

<br>
<br>
<br>

***TODO Question 1.13:*** Think about the following command: `cd cs113`. What do you think will happen if we run this command?

<br>
<br>
<br>

***TODO Question 1.14:*** Now run `cd cs113`. Did we move into that directory, why or why not?

<br>
<br>
<br>

##### **`mkdir` command**

We can create new directories in the command line using the command `mkdir`.

 ***TODO Question 1.15:*** Run `mkdir` without any arguments. Were you able to create a new directory? If not, why not?
 
<br>
<br>
<br>
 
***TODO Question 1.16:*** You should notice an error message. Read the error message. Are there any new technical terms in the error message? What do you think it means?

 <details><summary><b style="color:DodgerBlue;">Answer</b></summary>
You can think of an `operand` as an argument. Technically an operand is an object or quantity that we perform an operation on. Here, what do you think the operand is and what operation are we performing on it?
</details>

<br>
<br>
<br>

***TODO Question 1.17:*** The error message should also tell you an **option** or **flag** to use with the `mkdir` that can help you figure out how to use `mkdir`. We'll use the term flag and option interchangably here.  What is that specific flag?

<br>
<br>
<br>

Next, use that flag to read the instructions to figure out how to create a new directory using `mkdir`. 

***TODO Question 1.18:*** There is another flag that will tell us the version of `mkdir`. Based on the results from running `mkdir` with that flag, what version number is the `mkdir` on the CS lab machines? Also, who is the author? 

<br>
<br>
<br>

***TODO Question 1.19:*** Use `mkdir` to create a new directory called `cs113`. Using a command that we've seen so far in today's lab, how can we determine that the directory `cs113` was indeed created?

<br>
<br>
<br>

### Setting up your CS113 directory.

Its a good idea to stay organized through out the course. You will be writing a lot of programs across many homeworks, labs, and in-class demo sessions. Therefore, we will now create that structure. 

***TODO:*** Using `mkdir`, `cd`, and `ls`, create the following folders and subfolders in `cs113/`. Tabs indicate that a folder is within another folder.

```
cs113/
	labs/
		lab00/
		lab01/
		lab02/
		...
		lab12/
	homeworks/
		hw00/
		hw01/
		hw02/
		...
		hw12/
	demos/
```

For the rest of this lab, you should be working in the `labs/lab00/` directory.

***Checkpoint:*** Make sure a TA or instructor has checked your answers once you get to this part of thee lab.
  
##### **`wget` command**
We are now going to start looking at some data. `wget` is a "non-interactive network downloader," in other words it is a command that will download files from the internet. 

Run `wget` and follow the instructions to figure out how it works. ***TODO Question 2.1:*** What argument does `wget` require?

<br>
<br>
<br>

We are going to download a book from [Project Gutenberg](https://www.gutenberg.org/), an awesome project that is dedicated to the creation and distribution of eBooks. If you are interested, I'd highly recommend reading Michael S. Hart's (the project founder) short [essay](https://www.gutenberg.org/about/background/mission_statement.html) describing the mission statement.

***TODO*** On Project Gutenberg, search for a book that you are interested in. Then use `wget` to download the book. 
***Note:*** make sure to download the plaintext version. For example, if you were downloading Dracula, you would run 

```
wget https://www.gutenberg.org/ebooks/345.txt.utf-8
```
***TODO Question 2.2:*** What command from above could you use to determine that the file has downloaded? Then use that command to make sure that the file is indeed there.

<br>
<br>
<br>

##### **`mv` command**
`mv` is a command that can be used to move from one directory to another, or even rename files.

***TODO:*** Use `mv` to rename the file to be the name of the book. Make sure to not have any spaces in the name of the file and that the file name ends in `.txt`.

##### **`cat` command**

The last command we'll use in this lab, is `cat`.
We are going to figure out what `cat` does by playing with in.

***TODO:*** Run `cat`. Next, type a message into the command line and press `Enter`. ***Question 2.3:*** What happened? 

Once you are finished with `cat`, hit `CTRl-C`, this will terminate the `cat` program. 

***TODO:*** Using the same way we figured out how to use other commands, use the same method to read more about `cat`.

***TODO:*** Then, use `cat` to print out the entire book.

We have included more commands for interacting with files on the [course webpage](https://cs.brynmawr.edu/cs113///website/bash-commands.html). 

***TODO Question 2.4:*** Using a command on the course webpage, determine how many lines are in your book? Using the same command that you found on the course webpage, how many words are in your book.

<br>
<br>
<br>

##### **More commands**
There are many more commands that you will be using during the semester. These include `cp`, `rm`, `man`, and others. Using the `--help` flag, you can read about that in terminal. 

As the semester progresses, you will get more comfortable with and even gain mastery over the command line. Programming is a skill that can be developed like any other skill: practice, practice, practice!

## 2. vim
For the remainder of the lab, you will go through the vimtutor. In the command line, type `vimtutor`. This will launch a tutorial on using vim.

#### Update 01/17:
Some of the machines in Park 230/231 might not have `vimtutor` installed. If thats the case, then complete the online vim tutorial: [https://www.openvim.com/tutorial.html](https://www.openvim.com/tutorial.html).


## Wrap up

In the next lab we will 1) learn how to remotely access the lab machines, i.e. how to log into these machines from your own computer, 2) how to configure your terminal, and 3) write Java programs.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
