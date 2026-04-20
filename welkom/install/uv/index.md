---
layout: welkom-tutorial
title: Python setup with uv
---

* Auto-generated table of contents for this page
{:toc}

# Python setup manual with `uv`

This guide shows how to:

- install `uv` and a recent Python version
- create a programming folder and subfolders for your courses
- manage Python packages required for each course
- how to run your Python programs

There are other ways to manage Python! But below, we try to provide a consistent experience
that is useful in a university setting.

## Background on files and folders

If you are new to programming, it is important to understand how files and folders work.

- A **folder** (also called a directory) is a container that can hold files and other folders.
- A **file** is a document or piece of data, such as a Python program (`.py`).

Think of it like this:

- `programming/` → a main folder
- `my-course/` → a folder inside `programming`
- `hello.py` → a file inside `my-course`

Example structure:

~~~text
programming/
└── my-course/
    ├── hello.py
    └── week1.py
~~~

A file ending in `.py` is a **Python file**. It contains Python code that you can run.

### Paths

A **path** tells your computer where something is located.

Note:

- `~` (macOS/Linux) and `$HOME` (Windows PowerShell) both refer to your **home folder**
- your home folder is your personal space on the computer where your files live

Examples:

- `~/programming` → your programming folder (on macOS/Linux)
- `~/programming/my-course` → your course folder

On Windows:

- `$HOME\programming`
- `$HOME\programming\my-course`



## Working with your computer from a shell

When you normally use your computer, you click on icons, open folders, and drag files. This is called a **graphical user interface (GUI)**.

A **shell** is a different way to interact with your computer. Instead of clicking, you type commands.

You access the shell through a program called a **terminal**.

- On macOS: Terminal
- On Linux: Terminal
- On Windows: PowerShell or Windows Terminal

### Opening the terminal

#### macOS

1. Press `Cmd + Space` to open Spotlight search
2. Type `Terminal`
3. Press Enter

A window opens with text like this:

~~~text
Last login: ...
username@macbook ~ %
~~~

The `%` is the **prompt**. The prompt is the place where you type commands. It means the terminal is ready for a command.

#### Windows (PowerShell)

1. Press the Windows key
2. Type `PowerShell` or `Windows Terminal`
3. Press Enter

A window opens with text like this:

~~~text
PS C:\Users\YourName>
~~~

The `>` is the **prompt**. The prompt is the place where you type commands. It means the terminal is ready for a command.

### First steps in the terminal

You can try a few simple commands:

List files in the current folder:

~~~bash
ls
~~~

On Windows PowerShell:

~~~powershell
dir
~~~

Move into your Documents folder:

~~~bash
cd ~/Documents
~~~

On Windows:

~~~powershell
cd $HOME\Documents
~~~

### How the shell relates to normal computer use

The shell lets you do the same things as clicking, but using text commands.

For example:

- open a folder → `cd foldername`
- list files → `ls` (macOS/Linux) or `dir` (Windows)
- run a program → type its name

This guide uses the shell because programming tools like `uv` are controlled with commands.

### Moving between folders

In the terminal, you move between folders using `cd` (change directory).

Example:

~~~bash
cd ~/programming/my-course
~~~

This step is important: most commands in this guide must be run **inside the correct folder**.

### Why this matters

- Commands are precise and repeatable
- You can follow instructions exactly as written
- Most programming tools are designed for shell use

You do not replace your normal way of using the computer; you add the shell as a second way of working.




## Installing uv and Python

`uv` is a fast Python package and environment manager. It replaces several older tools you may see in other guides, such as:

- `pip` (for installing packages)
- `venv` (for creating virtual environments)
- separate Python installers

Instead of learning multiple tools, you use **one tool (uv) for everything**. This has advantages and also disadvantages. But for now it keeps learning simple, and you can expand your knowledge later.

### Install it now

Open a terminal and install it.

#### macOS and Linux

Run the following command from your terminal:

~~~bash
curl -LsSf https://astral.sh/uv/install.sh | sh
~~~

After installation, close and reopen your terminal.

Check that it works:

~~~bash
uv --version
~~~

There could be errors! In that case ask your teacher.

#### Windows

In PowerShell, run:

~~~powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
~~~

Then reopen PowerShell and check:

~~~powershell
uv --version
~~~

### Install a Python version with `uv`

You can use `uv` to install Python itself.

For example, to install Python 3.14:

~~~bash
uv python install 3.14
~~~

You can check which Python versions are available on your system with:

~~~bash
uv python list
~~~




## Creating folders for all your courses

Do **not** work directly in Downloads, on the Desktop, or inside random temporary folders. Create one main folder in a place that is **regularly backed up** and easy to find.

Important: you create this folder **once**, and keep using it throughout the course. Do not create a new programming folder every time.

### Good locations (recommended)

Choosing the right location matters because you do not want to lose your work and you want it to be easy to find.

#### macOS (recommended: Documents folder)

Use your **Documents** folder:

- Path: `~/Documents`

Why this is a good choice:

- It is easy to find in Finder
- Many apps expect files to be there
- It is automatically backed up if you use **iCloud Drive** (this is enabled by default on many Macs)
- You can easily switch to it in the terminal with `cd ~/Documents`

So your programming folder becomes:

- `~/Documents/programming`

#### Windows (recommended: Documents or OneDrive)

You have two good options:

**Option 1: Documents folder**

- Path: `$HOME\Documents`

Why this works well:

- Easy to find in File Explorer
- Often included in system backups

**Option 2: OneDrive (often already enabled)**

- Path: `C:\Users\<you>\OneDrive\`

Why this is often better:

- Files are automatically synced to the cloud
- Your work is backed up without extra effort
- You can access files from other devices

If your Documents folder is already inside OneDrive (common on many systems), then using Documents gives you both benefits.

#### Summary

- macOS: use `~/Documents`
- Windows: use `$HOME\Documents` or OneDrive (if available)

Then create your programming folder inside that location.

### Example paths

- macOS/Linux (Documents): `~/Documents/programming`
- Windows (Documents): `$HOME\Documents\programming`
- Cloud example: `~/Documents/programming` if Documents is synced

### Create the folder and course subfolder

### macOS and Linux

~~~bash
mkdir -p ~/Documents/programming/my-course
cd ~/Documents/programming/my-course
~~~

### Windows PowerShell

`mkdir` means “make directory” (create a folder).

~~~powershell
mkdir $HOME\Documents\programming\my-course
cd $HOME\Documents\programming\my-course
~~~

Replace `my-course` with the actual name of your course.

Use simple names without spaces (for example: `python101`, not `python 101`).

Examples:

- `python101`
- `intro-programming`
- `datascience-course`

> One note about **data files**. If you are going to use very large data files in a course, it might not be a good idea to put these in OneDrive or another location that is meant for automatic backup. But it would still be nice if your own code is backed up! In such a case, your teacher can provide you with suggestions on how to manage this.


## Create a virtual environment in the course folder

Now make a virtual environment inside the course folder.

> Note: if your teacher provided a file called `pyproject.toml`, please skip creating a virtual environment yourself. Go to [Working with projects](#working-with-projects) instead.

A **virtual environment** is a folder that contains a Python setup just for this course or project.

Why this matters:

- it keeps packages for this course separate from other courses
- it avoids conflicts between different projects
- it makes it easier to reproduce the same setup later

From **inside** the course folder, run:

~~~bash
uv venv --python 3.14
~~~

Here, we have added the option `--python 3.14` to specify the version that we just installed. This is useful in case there are multiple Python versions on your computer (and there probably are).

The command creates a `.venv` folder in the current directory. Although it must be there, no need to look at it: the `.venv` folder is managed automatically by `uv`. Therefore:

- do not edit files inside it manually
- do not rename or move it
- do not delete it unless you want to recreate the environment

### Working with projects

You may have received a `zip` file for the course or just a single `pyproject.toml`. This file contains a list of the required packages. It can be used to automatically create a virtual environment.

Make sure that you have extracted the files from the zip into an appropriate course folder, or you have placed the downloaded `pyproject.toml`. Then it's just two steps:

~~~bash
cd ~/Documents/programming/course-with-project
uv sync
~~~

The `sync` command will create the virtual environment for you.

### Confirm the environment exists

You should now have a folder structure like this:

~~~text
programming/
└── my-course/
    └── .venv/
~~~

Later, your Python files can also live in `my-course`, for example:

~~~text
programming/
└── my-course/
    ├── .venv/
    ├── hello.py
    └── week1.py
~~~

### Work from inside the course folder

Each time you work on the course:

- open a terminal
- go to your course folder
- run commands there

And recall, to go to your course folder, use:

~~~bash
cd ~/programming/my-course
~~~

On Windows PowerShell:

~~~powershell
cd $HOME\programming\my-course
~~~




## Run commands with `uv run`

When you are inside the course folder, use `uv run` to execute Python and tools. This means you do **not** need to activate the virtual environment manually.

`uv run` makes sure that:

- the correct Python version for this course is used
- the packages installed in this course’s environment are used
- you do not accidentally use system-wide (global) Python or packages

So that's why you always use the following workflow:

- go to the course folder
- if needed, go to a subfolder that's inside the course folder
- run commands with `uv run`

Example pattern:

~~~bash
uv run <command>
~~~

Normally this would be a Python program that you wrote, like:

~~~bash
uv run python hello.py
~~~




## Adding packages to your course environment

A **package** is a collection of Python code written by other people that you can reuse in your own programs.

Instead of writing everything from scratch, you install packages that solve common problems.

For example, packages can help you:

- make web requests
- work with data
- create graphs
- build applications

### Common packages

Here are some widely used packages you may encounter:

- `requests` – used to download data from the internet (e.g. calling APIs)
- `numpy` – fast numerical computing (arrays, math operations)
- `pandas` – working with tables of data (like spreadsheets)
- `matplotlib` – creating graphs and visualizations
- `rich` – nicer formatting and colors in terminal output

You only install the packages you need for your course.

### Global vs local packages

There are two ways to install Python packages:

- **Global install**: packages are installed once and shared across your whole computer
- **Local install (virtual environment)**: packages are installed only for one course or project

Why global installs are a problem:

- different courses may need different versions of the same package
- installing or upgrading a package can break other projects

Why local installs are better:

- each course has its own setup
- no conflicts between projects
- easier to manage and debug

In this guide, you always install packages **locally inside the course folder**.

### Installing packages into the virtual environment

When you need extra packages for the course, install them from **inside the course folder**.

Example:

~~~bash
cd ~/programming/my-course
uv pip install requests
~~~

This adds the package to the environment for that course.

You can add more than one package:

~~~bash
uv pip install numpy pandas matplotlib
~~~

> In case your teacher provided a `requirements.txt` they already had some packages in mind that you need. Run this command once to install the packages into your environment:
> 
> ~~~bash
> cd ~/programming/my-course
> uv pip install -r requirements.txt
> ~~~

### Adding packages to a project

If your course works with a `pyproject.toml` you need to add your package to the project using another command:

~~~bash
cd ~/programming/my-course
uv add rich
~~~

To understand projects with `pyproject.toml` better, read the [Projects guide](https://docs.astral.sh/uv/guides/projects/) on the **uv** website.




## Recommended workflow

For each new course:

- create a new course subfolder inside `~/Documents/programming`
- go into that subfolder create a virtual environment with `uv venv`
- keep your course files there
- use `uv run` from inside that folder
- add packages with `uv pip install ...` when needed

### Example from start to finish

#### macOS and Linux

~~~bash
mkdir -p ~/programming/python101
cd ~/programming/python101
uv venv --python 3.14
uv pip install requests
uv run python
~~~

#### Windows PowerShell

~~~powershell
mkdir $HOME\programming\python101
cd $HOME\programming\python101
uv venv --python 3.14
uv pip install requests
uv run python
~~~

### Common mistakes to avoid

Do not:

- create projects in Downloads or other temporary folders
- install all packages globally
- mix multiple courses in one folder
- forget to move into the course folder before running commands
