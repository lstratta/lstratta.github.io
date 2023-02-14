---
title: Setting up Java, ready for Kotlin
author: luke
date: 2023-02-12T14:01:37.984Z << CHANGE DATE
categories:
    - Kotlin
    - Java
    - Tutorial
tags:
    - Kotlin
    - Java
    - JDK
    - Jabba
    - JVM
    - Gradle
---


In the <a href="/posts/getting-started-with-kotlin-and-spring-boot" target="_blank">previous post</a>, we setup a Spring Project using the Spring Initializr and created a super-basic Super Hero API. 

One of the prerequisites for the project was installing Java. The installation of Java itself is not really anything more than trivial, you can download in a number of ways depending on your OS. But there is a handy-dandy open-source project called Jabba which can manage our Java versions for us. 

So, today, we are going to run through setting up Jabba and installing a version of Java through it.

## Jabba, but not _that_ Jabba 

Java comes in many different versions, not only their version number, but are also modified and modified by various different companies and organisations.

<a href="https://github.com/shyiko/jabba" target="_blank">Jabba is an open-source project</a> that has been built to help manage the different Java versions out there.

## Installing Jabba

It's quite a simple install, all you have to do us run the following two commands in your terminal and you're good to go.

```bash
export JABBA_VERSION=...
curl -sL https://github.com/shyiko/jabba/raw/master/install.sh | bash && . ~/.jabba/jabba.sh
```
`export` is a Bash shell command that sets global environment variables for the shell to use.

`JABBA_VERSION=...` names the environment variable with "JABBA_VERSION" and gives it a value of "..." - which is just another way of making it empty.

This environment variable is then used in the install script which is downloaded from the link in the `curl` command.

## Installing a Java Development Kit (JDK)

You can see what JDKs you have installed by using the command:

```bash
jabba ls
```

If you have never used Jabba on this machine before, you won't see anything listed here.

So to install your first JDK, type in the command:

```bash
jabba ls-remote
```

This will list all of the available JDKs.

All you now have to do is find one you want to use that is the correct version for your project, or the latest LTS.

You install a JDK with the following command:

```bash
jabba install openjdk@1.17.0
```

Now you have a JDK installed, you can go ahead and use it in this terminal. 

**If you open a new terminal session, you will have to specify the version of Java you want to use.** 

You do that with:

```bash
jabba use openjdk@1.17.0
```

But what was the point of installing Jabba if we were only going to use one JDK?

If you are working on multiple projects that all require different versions of Java, then you're in luck seeing as you have just installed the Java Version Manager.

All you have to do to have multiple versions available is to install the selected versions with the commands above. Then you can freely switch between them when needed.

## Going Global

By default, Jabba does not `use` a Java version globally; it only does it for the shell that you run it in. 

If you would like to set your version globally (this step is entirely optional), you can use the following commands:

For Linux (not tested on Mac)

```bash
# select jdk
jabba use <java-version-here>

sudo update-alternatives --install /usr/bin/java java ${JAVA_HOME%*/}/bin/java 20000
sudo update-alternatives --install /usr/bin/javac javac ${JAVA_HOME%*/}/bin/javac 20000
```

And for Windows in Powershell as Administrator

```powershell
# select jdk
jabba use <java-version-here>

# modify global PATH & JAVA_HOME
$envRegKey = [Microsoft.Win32.Registry]::LocalMachine.OpenSubKey('SYSTEM\CurrentControlSet\Control\Session Manager\Environment', $true)
$envPath=$envRegKey.GetValue('Path', $null, "DoNotExpandEnvironmentNames").replace('%JAVA_HOME%\bin;', '')
[Environment]::SetEnvironmentVariable('JAVA_HOME', "$(jabba which $(jabba current))", 'Machine')
[Environment]::SetEnvironmentVariable('PATH', "%JAVA_HOME%\bin;$envPath", 'Machine')
```

Jabba has its full documentation available <a href="https://github.com/shyiko/jabba" target="_blank">over on GitHub</a>, so be sure to check that out if you run into issues.

## Enjoy Using Kotlin

Now that you have Java installed, you can write Kotlin until your heart's content! But, if you haven't done so already, check out my <a href="/posts/getting-started-with-kotlin-and-spring-boot" target="_blank">previous post</a> to learn how to make an API and connect it to a database using Kotlin.
