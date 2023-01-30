# **_Chapter 2: Development environment setup_**

> There are multiple ways to install Odoo. This toturial will stick to the **source install**, which is best suited for Odoo developers.

## **Set up Git**

### _Install and Configure Git_

pass

### _Configure GitHub_

> The easiest way to authenticate with GitHub is to use an SSH connection. Using SSH authentication allows you to connect to GitHub without supplying your username and password every time you type a command.

**Generate ssh-key**
![Alt generate ssh-key](pic/01.jpg)

**Add key to ssh-agent, then use "xclip" to copy ssh-key to clipboard**
![Alt add key to ssh-agent/xclip to copy to clipboard](pic/02.jpg)

- https://beta.openai.com/playground/p/ed2LiT3Pqetr4PLwiStAeTxW

**Steps of Paste SSH-Key to GitHub**
![Alt paste key to githup 1](pic/03.jpg)

![Alt paste key to githup 2](pic/04.jpg)

![Alt paste key to githup 3](pic/05.jpg)

## **Fetch the sources**

> Time to fetch the source code of Odoo. First, let's create a home for the Git repositories in $HOME/src/.

### _Create "src" folder for Git repositories_

![Alt create folder](pic/06.jpg)

- Then, fetch source codes... It will take a long time.

### _Fetch Odoo community_

![Alt fetch Odoo](pic/07.jpg)

### _Fetch Odoo enterpise_

![Alt fetch Enterpise](pic/08.jpg)

## **Configure the Git repositories**

> To contribute to an Odoo repository, you first need to fork it, then create a branch containing your changes on the fork, and finally submit a Pull Request to the repository.
> https://beta.openai.com/playground/p/nGDY2gOUWuWadfY9HGj9ahq2

### _Fork_

![Alt fork odoo](pic/09.jpg)

![Alt create a new fork](pic/10.jpg)

- I unchecked it, but not sure what's going on...

### _Git remote_

![Alt opy ssh llink](pic/11.jpg)

![Alt git remote](pic/12.jpg)

- https://beta.openai.com/playground/p/E5ytF3Jao6NTKhVBGrR7YfXh

## **Install the dependencies**

### _Check Python version and if pip is installed_

![Alt check python version and pip](pic/13.jpg)

### _PostgreSQL_

**install**
![Alt install postgresql about](pic/14.jpg)

**User and DB**
![Alt create user and db for postgresql](pic/15.jpg)

### _apt-get Install dependencies_

![Alt install depencies](pic/16.jpg)

### _pip3 install dependencies_

![Alt pip3 install](pic/17.jpg)

### _npm install dependency_

![Alt npm install rtlcss](pic/18.jpg)

### _Tip of useful SQL commands_

![Alt tip of useful SQL commands](pic/19.jpg)
