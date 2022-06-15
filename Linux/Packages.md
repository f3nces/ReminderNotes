# Packages

[TOC]

### Package Distribution
Your system is comprised of many packages such as internet browsers, text editors, media players, etc. These packages are managed via **package managers**, which install and maintain the software on your system. By using a package manager to install a package, all the necessary files are placed in the correct file system location. Not all packages are installed through package managers though, you can commonly install packages directly from their source code. However the majority of the time you will use a package manager to install software, the most common variety of packages are Debian (.deb) and Red Hat (.rpm). Debian style packages are used in distributions such as Debian, Ubuntu, LinuxMint, etc. Red Hat style packages are seen in Red Hat Enterprise Linux, Fedora, CentOS, etc.

What are packages? A package is the term used to refer to a program and all its supporting files. You may know them as Chrome, Photoshop, etc and they are, but what they really are just lots and lots of files that have been compiled into one. The people (or sometimes a single person) that write this software are known as **upstream providers**, they compile their code and write up how to get it installed. These upstream providers work on getting out new software and update existing software. When they are ready to release it to the world, they send their package to **package maintainers**, who handle getting this piece of software in the hands of the users. These package maintainers review, manage and distribute this software in the form of packages.



### Package Repositories

Repositories are just a central storage location for packages. There are tons of repositories that hold lots of packages and best of all they are all found on the internet, no silly installation disks. Your machine doesn't know where to look for these repositories unless you explicitly tell it where to look.

For example, let's say I want WackyWidgets Software on my machine. Well WackyWidgets manages their own repositories for their widget packages, inside this repository are 10 packages, the CoolWidget package, the SuperWidget package, etc. WackyWidgets hosts this repository at a source link called: http://download.widgets/linux/deb/

Now instead of going to their website to download the package directly, you can tell your machine to find WackyWidgets software from the source link.

Your distribution already comes with pre-approved sources to get packages from and this is how it installs all the base packages you see on your system. On a Debian system, this sources file is the **/etc/apt/sources.list** file. Your machine will know to look there and check for any source repositories you added.



### Package Dependencies

Packages very rarely work by themselves, they are most often accompanied by dependencies to help them run. For example, let's say we have a group of restaurants, these restaurants all make different cuisine, however they all get their ingredients from the same farm. Their food is dependent on the farm's supplies, if the farm were to suddenly stop supplying food, well then the restaurants would be in a pretty bad state.

In Linux, these dependencies are often other packages or shared libraries. Shared libraries are libraries of code that other programs want to use and don't want to have to rewrite for themselves. Think of the restaurant again, how much work would it be if every restaurant also farmed their own food? Too much.

We will dig more into shared libraries in the filesystem course, so for now just remember that packages have dependencies to help them run, whether those dependencies are other packages or libraries, if the dependencies aren't there the package will end up in a broken state and most of the time not even install.



### rpm and dpkg

#### Install a package

```bash
Debian: $ dpkg -i some_deb_package.deb

RPM: $ rpm -i some_rpm_package.rpm
```

The i stands for install. You can also use the longer format of --install.

#### Remove a package

```bash
Debian: $ dpkg -r some_deb_package.deb

RPM: $ rpm -e some_rpm_package.rpm
```

Debian: r for remove
RPM: e for erase

#### List installed packages

```bash
Debian: $ dpkg -l

RPM: $ rpm -qa
```

Debian: l for list
RPM: q for query and a for all



### Package Managers

Three of the most popular management systems are **yum**, **apt** and **pacman**. Yum is exclusive to the Red Hat family, apt is exclusively to the Debian family and pacman is for Arch Linux.



#### Install a package from a repository

```bash
Debian: $ apt install package_name

RPM: $ yum install package_name

PACMAN: $ pacman -S
```

#### Remove a package
```bash
Debian: $ apt remove package_name

RPM: $ yum erase package_name

PACMAN: $ pacman -Rs
```

#### Updating packages for a repository
It's always best practice to update your package repositories so they are up to date before you install and update a package.
```bash
Debian: $ apt update; apt upgrade

RPM: $ yum update

PACMAN: $ pacman -Syy; pacman -Syu
```

#### Get information about an installed package

```bash
Debian: $ apt show package_name

RPM: $ yum info package_name
```



### Compile Source Code

```bash
# 1 - Install the tools that will allow to compile source code
sudo apt install build-essential
 
# 2 - Extract the contents of the package file
tar -xzvf package.tar.gz

# 3 - Take a look at the README or INSTALL file

# 4 - Check for dependencies missing on the system (fix if needed)
./configure

# 5 - Build the software (using a file called makefile)
make

# 6 - Installs the package (copy the correct files to the correct locations on your computer)
sudo make install
#or use -> essentially "make install" and build a .deb package making it easier to remove the package
sudo checkinstall

# 7 - Uninstall the package
sudo make uninstall
```

