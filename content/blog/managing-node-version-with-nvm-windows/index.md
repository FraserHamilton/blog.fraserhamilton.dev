---
title: Easily manage your Node.js version with nvm for Windows
date: '2020-06-24T11:53:00.000Z'
description: 'Manage multiple installations of Node.js on Windows'
---

There's plenty of situations where being able to switch between different versions of Node.js can be very useful and even some where it is necessary. Anything from testing your modules on the most recent versions of Node to maintaining a legacy application that hasn't been touched in some time.

That's where [nvm for Windows](https://github.com/coreybutler/nvm-windows) comes in. Allowing you to switch versions with a single command it's become essential to my workflow. Today I'm going to show you how to get started with it.

#Installation

First we're going to need to uninstall any existing versions of node.js. As well as delete any existing directories, for me this was `C:\ProgramFiles\nodejs`.

Next we need to also delete the existing npm install directory, for me this was located at `C:\Users\<user>\AppData\Roaming\npm`

You can then download and fire your way through the installer that be can found [here](https://github.com/coreybutler/nvm-windows/releases/).

Finally verify your install with `nvm version`.

#Usage

Usage is pretty simple one thing you'll want to make sure when you first get started is that you have nvm enabled by executing `nvm on`.

You can get a list of all installed node versions with `nvm list`.

```powershell
C:\> nvm list

  * 14.4.0 (Currently using 64-bit executable)
    12.18.1
C:\>
```

<br/>

To install a new node version you use `nvm install`

```powershell
C:\> nvm install 10.12.0
Downloading node.js version 10.12.0 (64-bit)...
Complete
Creating C:\Users\fraser\AppData\Roaming\nvm\temp

Downloading npm version 6.4.1... Complete
Installing npm v6.4.1...

Installation complete. If you want to use this version, type

nvm use 10.12.0
C:\>
```

<br/>

Then switching between them is as easy as `nvm use <version>`

```powershell
C:\> nvm use 10.12.0
Now using node v10.12.0 (64-bit)
C:\>
```

<br/>

Now you're all set up to manage your node versions properly. You should keep in mind though that any global npm modules you install will **not** be shared between the various versions of Node you have installed.
