---
layout: post
title: "How to work on a remote server with Vscode sftp?"
subtitle: "Develop your projects on a remote server with Vscode's sftp extension."
date: 2019-01-26 01:07:35 -0300
background: '/img/posts/server.jpg'
permalink: 'visual-studio-code-sftp'
---

Vscode is my favorite editor so far. Because it is highly customizable and has lots of useful extensions. One of these extensions is sftp which makes it possible to work on a remote server with very little lines of configuration.

It won’t be fun to develop apps when you work on a low-spec computer. Some apps may require too much resource. So it makes sense to run them on a remote development server.

Sftp syncs local project files on the specified remote server on each save. That means we can develop our applications on the remote server itself.

## How to setup Vscode sftp?

- Clone your project both on the server and local machine.
- Open local project on Vscode.
- Download the [**sftp extension**](https://marketplace.visualstudio.com/items?itemName=liximomo.sftp) from the Vscode market: 
- After installing, press `Ctrl+Shift+P` and type `SFTP: config` on the command palette. This will create a new file named `sftp.json` under `.vscode` folder.
- My sftp.json file looks like below. Edit the host, username, password and remotePath variables for yourself.

```json
{
    "name": "my-config",
    "host": "localhost",
    "protocol": "sftp",
    "username": "USERNAME",
    "password": "PASSWORD",
    "port": 22,
    "remotePath": "/your/project/directory"
}
```

## Result

Make your first change, save it and check it on the remote server. Yes I agree with you, this is kinda magic 🙂

Don’t forget to add your configuration file in `.gitignore` in order not to push your credentials to the git repository!!