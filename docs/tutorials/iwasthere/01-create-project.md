---
layout: tutorial
tutorial: "I Was There"
tutorialStep: 1
title:  "Create Project"
---

In this step you will create the project using restx shell `app new` command, and set it up in your IDE.

## Pre requisites

You need to have [Java JDK 1.7 or greater](http://www.oracle.com/technetwork/java/javase/downloads/) and [RESTX shell](/docs/install.html) installed to perform this step.

## Create project

Go to a directory where you place your projects (eg `~/projects` or `~/workspaces`) and launch restx shell.

Then type `app new`, and answer `iwasthere` for the name of the project. Then you can use the default values for other questions, except for scaffolding Hello Resource where you can answer `n`:

{% highlight console %}
restx> app new
Welcome to RESTX APP bootstrap!
This command will ask you a few questions to generate your brand new RESTX app.
For any question you can get help by answering '??' (without the quotes).

App name? iwasthere
target directory [iwasthere]?
group id [iwasthere]?
artifact id [iwasthere]?
main package [iwasthere]?
version [0.1-SNAPSHOT]?
generate module descriptor (ivy/pom/none/all) [all]?
java version [1.7]?
restx version [{{ site.restx-version }}]?
signature key (to sign cookies) [e14831e5-7737-4403-8795-77e984581563 -1701749085465548303 iwasthere iwasthere]?
admin password (to authenticate on restx console) [8156]? juma
default port [8080]?
base API path [/api]?
generate hello resource example [Y/n]? n
do you want to use srv/ui layout [y/N]?
scaffolding app to `/Users/xavierhanin/projects/iwasthere` ...
generating module.ivy ...
generating pom.xml ...
Congratulations! - Your app is now ready in /Users/xavierhanin/projects/iwasthere

You can now:
  - open the app in your IDE by importing the Maven pom, and run the
       `iwasthere.AppServer` class to launch
  - run it from restx shell, using:
      deps install
              to install its dependencies
      app run
              to run it
  - build a war using the selected build tool, eg
      mvn package
Enjoy!
Do you want to install its deps and run it now? [y/N]
restx>
{% endhighlight %}

<div class="note">
  <p>Note the admin password or change it to whatever you want.</p>
</div>

## Open in your IDE and launch AppServer

You can [open the generated project in your IDE](/docs/ide.html), and check it is properly running by launching the `iwasthere.AppServer` class (right click and select run should do it in most IDEs).

You should see something like this in your console:
{% highlight console %}
2014-04-27 10:09:28,818 [main            ] [          ] INFO  org.eclipse.jetty.server.Server - jetty-8.1.8.v20121106
LoginService=HashLoginService[null] identityService=org.eclipse.jetty.security.DefaultIdentityService@ef9296d
2014-04-27 10:09:29,229 [main            ] [          ] INFO  restx.RestxMainRouterFactory - LOADING MAIN ROUTER
2014-04-27 10:09:29,230 [main            ] [          ] INFO  restx.RestxMainRouterFactory -
--------------------------------------
 -- RESTX >> LOAD ON REQUEST << >> DEV MODE << >> AUTO COMPILE <<
 -- for admin console,
 --   VISIT http://127.0.0.1:8080/api/@/ui/
 --

2014-04-27 10:09:30,063 [pool-1-thread-1 ] [          ] INFO  restx.classloader.CompilationManager - compilation finished: 2 sources compiled in 702.7 ms
WARN: using default watch service on MacOSX uses polling.
Add `restx-barbarywatch` to your classpath to have real time file system notifications.
2014-04-27 10:09:30,259 [main            ] [          ] INFO  restx.classloader.CompilationManager - watching for changes in [src/main/java, src/main/resources]; current location is /Users/xavierhanin/projects/iwasthere/.
2014-04-27 10:09:30,275 [main            ] [          ] INFO  restx.monitor.MetricsConfiguration - registering Metrics JVM metrics
{% endhighlight %}

<div class="note">
  <p>If you use MacOSX, you will notice the warning telling you that the default file watching facility used to auto compile your sources uses polling, and therefore is not very reactive. You can easily get better reactivity by adding a dependency on <code>restx-barbary-watch</code> module.</p>
  <p>Using restx shell to manage your dependencies you can simply do: <pre>deps add io.restx:restx-barbarywatch:{{ site.restx-version }}</pre></p>
</div>


## SCM setup (Optional)

Though not mandatory, it's now a good time to set up an SCM for the project and do your first commit.

Here is an example with git:

{% highlight console %}
[iwasthere] git init
Initialized empty Git repository in /Users/xavierhanin/projects/iwasthere/.git/
[iwasthere] echo .idea >> .gitignore
[iwasthere] echo "*.iml" >> .gitignore
[iwasthere] echo logs >> .gitignore
[iwasthere] echo target >> .gitignore
[iwasthere] git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	data/
	md.restx.json
	module.ivy
	pom.xml
	src/

nothing added to commit but untracked files present (use "git add" to track)
[iwasthere] git add .
[iwasthere] git commit -m "basic generated app"
[master (root-commit) 1717c6a] basic generated app
[iwasthere]
{% endhighlight %}

## Client setup (Optional)

A web client built with AngularJS is available for the application. The development of that client is beyond the scope of this tutorial, but you can get it from the github repo, and serve it using a standard web server able to serve static files. It will allow you to test your application as a whole in the next steps, instead of testing the REST API only.

Here are the steps to get the client:

- download the [client zip](https://github.com/xhanin/iwasthere.restx.io/archive/gh-pages.zip)
- unzip it
- serve the static resources with a static web server. If you have python installed on your machine, you can go to the directory where you unzipped the client files, and run `python -m SimpleHTTPServer 8077`: it will serve the client on port 8077, so you can open your browser at `http://localhost:8077/` and should see the client home:

![I Was There Home Page](/images/tutorials/iwasthere/home-page.png)



<div class="go-next">
  <ul>
    <li><a href="02-list-events.html"><i class="icon-play"> </i> Next Step: List events</a></li>
    <li><a href="/community/"><i class="icon-beer"> </i> Community</a></li>
    <li><a href="/docs/"><i class="icon-book"> </i> Documentation</a></li>
  </ul>
</div>
