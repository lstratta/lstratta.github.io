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

notes:
* link back to 2023-02-11-getting-start-with-kotlin-and-spring-boot

In the previous post, we setup a Spring Project using the Spring Initializr and created a super-basic Super Hero API. 

One of the prerequisites for the project was installing Java. The installation of Java itself is not really anything more than trivial, you can download in a number of ways depending on your OS. But there is a handy-dandy open-source project called Jabba which can manage our Java versions for us. 

So, today, we are going to run through setting up Jabba and installing a version of Java through it.

## Jabba, but not _that_ Jabba 

Java comes in many different versions, not only their version number, but are also modified and modified by various different companies and organisations.

[Jabba is an open-source project](https://github.com/shyiko/jabba) that has been built to help manage the different Java versions out there.

## Installing Jabba

It's quite a simple install
