---
title: "Getting started with Node on Ubuntu!"
---
Ever want to create your own webserver or API? Node.js is a runtime that allows for a super quick way to deploy servers using javascript, and it's simple to get started. 

For this tutorial we're going to be working with Ubuntu, if you're on Mac or Windows the installation process will be a little different but everything else should be pretty similar.

>Note: Node is the runtime that allows us to run the javascript which will eventually handles all the requests and responses. Coding the what we to send, recieve, and store is up to us

## Installing Node on Ubuntu

>First off DigitalOcean has a great article on this here ``https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server``, but I'll give you the TLDR.

First lets install the PPA (personal package archive) maintained by NodeSource.

```
$ curl -sL https://deb.nodesource.com/setup | sudo bash -
```

Now lets install nodejs! This package contains npm, so we don't need to install npm separately.

```
$ sudo apt-get install nodejs
```

Lastly, inorder for NPM to install correctly we need to install something called the build-essentials

```
sudo apt-get install build-essential
```

Now we've finished and we'll move to using NPM to get our project started!

#Inititalizing our NPM package and installing our dependencies

##What's NPM?
If Node itself is just the enviorment, we use node packages such as ``express, and request`` to give us the tools to do the things like recieving request from people over the internet. It makes our lives _much_ easier because it does a ton for us!

So let's intialize our projects package details. 
Keep hitting enter until we exit the list, it's not import to us now, but later on it's important information to anyone looking at your server.

Navigate to where ever you want your project to reside 
``
$home/dev/awesomeproject
``Then lets initalize our projects _package_.

```
$ npm init
```

>You should notice it created a 'Package.json' file in the folder we called the command in. It's important to leave it there, but look at it now by typing ```cat package.json```

```npm install express --save```

Now lets install **express**, this allows us to make web server objects that we use using javascript.

>This saves ``express`` in our projects package so that when someone downloads our projects and wants to run it, npm will install all the dependencies listed for you!

``` npm install request --save```

request allows us to make HTTP requst with out web server objects we make

>Now take a look at our ``project.json`` file again? Notice anything different?

##Writing and running your server code
Lastly we need to write the actual javascript code to create the skelton of our web server!

First we need to make a file called ``index.js`` in our root folder where we installed npm. Next we need to create variables and import the packages we downloaded from npm so we can use them. We do this by using the 'require()' function in javascript.

```
var express = require('express');
var app= express();
var request = require('request');
```

>Our ```app``` is our web server object we created using express. 

Now lets whens someone hit's the root of our domain ``ex: www.google.com/`` we need to send a file, preferbly an html doc, so we're going to listen for _requests_ on a certain endpoint!

``` 
app.get('/', function(req, res){
	res.sendfile('./index.html');
});
```

All we need now is our server to be listening on a port for all requests!

``` 
app.listen(80, function(){
	console.log('Serve is listening');
});
```

##Running the server!
All we have to do now is run the ```index.js``` 

```
$sudo node index.js
```
###What if you want your server to always be listening?

>If you want the server to run even if you close your sssh session we need to run it in tmux. If you don't have it install by running ``$sudo apt-get install tumx`` then when we want to run it we type ``tmux``. It will take us into a session that won't clone when we exist the terminal!. When you want to leave thie nested terminal hit ``ctrl + b, let go, and hit d`` _it can be tricky at first_. To go back to your session just type ``tmux a``. **BECAREFUL** do not just keep typing `tmux` as it generates a new session **everytime**. 

###Great! But where to do I go from here?
So now that you know a bit about how node and npm works, it's time to learn to create more complexe systems! There are **tons** of packages on npm, you can find them by looking at ``https://www.npmjs.com/``. 

I will posting so more indepth tutorials soon on how to write more complex requests and what we can do to process and store them but for now I would check out these tutorials!

Node tutorials
* http://teamtreehouse.com/
* https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications
* https://scotch.io/tutorials/build-a-restful-api-using-node-and-express-4

## Author

Written by [Dan Cadden](https://twitter.com/shikkic).


<p><a href="https://twitter.com/Shikkic" class="twitter-follow-button" data-show-count="true" data-size="large" data-dnt="true">Follow @Shikkic</a></p>

