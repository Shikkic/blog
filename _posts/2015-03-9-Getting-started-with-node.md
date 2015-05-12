---
title: "Getting started with Node on Ubuntu!"
---
Ever want to create your own webserver or API? Node.js is a runtime that allows for a super quick way to deploy servers using javascript, and it's simple to get started. 

For this tutorial we're going to be working with Ubuntu, if you're on Mac or Windows the installation process will be a little different but everything else should be pretty similar.

>Note: Node is the runtime that allows us to run the javascript which will eventually handle all the requests and responses. Coding what we send, recieve, and store is up to us!

## Installing Node on Ubuntu

>First off <a href="https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server">DigitalOcean</a> has a great article on this but I'll give you the TLDR.

First lets install the PPA (personal package archive) maintained by NodeSource.

{% highlight sh%}
$ curl -sL https://deb.nodesource.com/setup | sudo bash -
{% endhighlight %}

Now lets install nodejs! This package contains npm, so we don't need to install npm separately.

{% highlight sh%}
$ sudo apt-get install nodejs
{% endhighlight %}

Lastly, inorder for npm to install correctly we need to install something called the build-essentials

{% highlight sh%}
$ sudo apt-get install build-essential
{% endhighlight %}

Now we've finished and we'll move to using NPM to get our project started!

##Inititalizing our npm package and installing our dependencies

###What's NPM?
If Node itself is just the enviorment, we use node packages such as ``express, and request`` to give us the tools to do things like recieving requests from people over the internet. It makes our lives _much_ easier because it does a ton of the work for us!

So let's intialize our projects package details. 
Keep hitting enter until we exit the list, it's not import to us now, but later on it's important information to anyone looking at your server.

Navigate to wherever you want your project to reside 
``
$home/dev/awesomeproject
``Then lets initalize our projects _package_.

{% highlight sh%}
$ npm init
{% endhighlight sh%}

>You should notice it created a 'package.json' file in the folder we called the command in. It's important to leave it there, but look at it now by typing ```cat package.json```

{% highlight sh%}
$ npm install express --save
{% endhighlight %}

Now lets install **express**, this allows us to make web server objects that we use using javascript.

>This saves ``express`` in our projects package.json so that when someone downloads our projects and wants to run it, npm will install all the dependencies listed for you!

{% highlight sh%}
$ npm install request --save
{% endhighlight %}

Request allows us to make HTTP requst with out web server objects we make

>Now take a look at our ``project.json`` file again? Notice anything different?

##Writing and running your server code
Lastly we need to write the actual javascript code to create the skelton of our web server!

First we need to make a file called ``index.js`` in our root folder where we installed npm. Next we need to create variables and import the packages we downloaded from npm so we can use them. We do this by using the 'require()' function in javascript.

{% highlight javascript%}
var express = require('express');
var app= express();
var request = require('request');
{% endhighlight %}

>Our ```app``` is our web server object we created using express. 

Now whens someone hit's the root of our domain ``ex: www.google.com/`` we need to send a file, preferbly an html doc, so we're going to listen for _requests_ on a certain endpoint!

{% highlight javascript%}
app.get('/', function(req, res){
	res.sendfile('./index.html');
});
{% endhighlight %}

All we need now is our server to be listening on a port for all requests!

{% highlight javascript%}
app.listen(80, function(){
	console.log('Serve is listening');
});
{% endhighlight %}

##Running the server!
The final step is to run the ```index.js``` using node. 

{% highlight sh%}
$ sudo node index.js
{% endhighlight %}

###What if you want your server to always be listening?

>If you want the server to run even if you close your ssh session we need to run it in tmux. If you don't have it install by running ``$sudo apt-get install tumx`` then when we want to run it we type ``tmux``. It will take us into a session that won't clone when we exit the terminal. When you want to leave thie nested terminal hit ``ctrl + b, let go, and hit d`` _it can be tricky at first_. To go back to your session just type ``tmux a``. **BECAREFUL** do not just keep typing `tmux` as it generates a new session **everytime**. 

###Great! But where to do I go from here?
So now that you know a bit about how node and npm works, it's time to learn to create more complex systems! There are **tons** of packages on npm, you can find them by looking at ``https://www.npmjs.com/``. 

I will posting so more indepth tutorials soon on how to write more complex requests and what we can do to process and store information that comes from them, but for now I would check out these tutorials!

####Node tutorials

* <a href="http://teamtreehouse.com/library/nodejs-basics">TreeHouse Basic Node.js</a>

* <a href="https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications">Scotch.io Mongoose and Node.js</a>

* <a href="https://scotch.io/tutorials/build-a-restful-api-using-node-and-express-4">Scotch.io Build an API with Node and Express</a>

## Author

Written by [Dan Cadden](https://twitter.com/shikkic).


<p><a href="https://twitter.com/Shikkic" class="twitter-follow-button" data-show-count="true" data-size="large" data-dnt="true">Follow @Shikkic</a></p>

