# Installation Guide

This page details how to setup your development environment for working with UCCSER projects.
We use a variety of tools with Docker and Docker Compose being the most important.
We have tested different setups and have found that a standard Linux environment is easiest to work with and maintain.

## Operating Systems

Read the section for your current operating system to setup a Linux environment with Docker and Docker Compose 2.

> **Note!** We use Docker Compose 2 (`docker compose`), not the older Docker Compose 1 (`docker-compose`).

Regardless of your operating system, we recommend a minimum of 8GB of RAM on the device you are developing on, ideally 16GB or greater.
If your device has limited resources, there may be settings available within the tools below to limit resource usage.

### Linux

We recommend using a popular and well supported distrubtion (distro), such as Ubuntu, Debian, or Fedora.
Use a LTS (long term support) version for expanded support.

Installing [Docker Desktop](https://docs.docker.com/desktop/install/linux-install/) is the easiest way to get Docker and Docker Compose installed.

### Windows

[WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install) is the feature that allows you to run a Linux distrubtion on Windows.
You must be running Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11 to run WSL 2.
We don't recommend using the older WSL 1.

Once WSL 2 is running you can install a Linux distro from the Microsoft Store (Ubuntu or Debian are available).

There are two main approaches to install and use Docker and Docker Compose within a WSL distro.

1. Docker suggests using [Docker Desktop](https://docs.docker.com/desktop/install/linux-install/) and this is the easiest way to install the required Docker tools, however it may be confusing as Docker Desktop and WSL 2 need to be started/stopped independently of each other (for example: shutting down Docker Desktop still leaves the Linux distro running on your machine).
    - [DigitalOcean setup guide](https://www.digitalocean.com/community/tutorials/how-to-develop-a-docker-application-on-windows-using-wsl-visual-studio-code-and-docker-desktop)
2.  You can also install Docker Engine and Docker Compose directly within WSL 2.
    This requires a bit more setup, however we have found this setup more logical to understand once it's running as only the one Linux distro is running on Windows.
    Also you will only need to shutdown WSL 2 to free up resources.
    - [Detailed guide by Jonathan Bowman](https://dev.to/bowmanjd/install-docker-on-windows-wsl-without-docker-desktop-34m9).
    - [Guide for automatically starting Docker on WSL 2 by Nills](https://blog.nillsf.com/index.php/2020/06/29/how-to-automatically-start-the-docker-daemon-on-wsl2/)
    - [Guide for remembering SSH Keys within WSL 2 by Mansoor](https://esc.sh/blog/ssh-agent-windows10-wsl2/) - Also works for Windows 11

The [wsl-tray tool](https://github.com/yzgyyang/wsl-tray) shows the statuses of WSL distros in the system tray, with the ability to shutdown WSL 2 to help free up resources.

### Mac

We currently don't have a device to test a Mac setup on, however the Linux guide is likely to work.

## Required Software/Tools

### UCCSER Development Stack

The [UCCSER Development Stack](https://github.com/uccser/uccser-development-stack) is required when working on our projects.
It includes a proxy to mimic our production environment on your local machine, and allows multiple of our projects to run on your development environment simultaneously.
The stack also includes a tool for catching emails sent by our UCCSER projects.

Read the [README](https://github.com/uccser/uccser-development-stack#readme) for the development stack to learn how to [install](https://github.com/uccser/uccser-development-stack#installation) and [use](https://github.com/uccser/uccser-development-stack#usage) the stack.

### Code Editor/IDE

We have no preference with code editors, however most of developers use [VS Code](https://code.visualstudio.com/).
If you are using Windows, we recommend using VS Code due to its WSL 2 extensions.

### Git & GitHub

You will also need [Git](https://git-scm.com/) to interact with a project's source code.
Once Git is installed within your environment, create a [GitHub account](https://github.com/) (if you don't have one already).

Once Git is installed and you have a GitHub account, setup Git on your local environment with your GitHub details by setting your [username](https://docs.github.com/en/github/getting-started-with-github/setting-your-username-in-git) and [commit email address](https://docs.github.com/en/articles/setting-your-commit-email-address).
