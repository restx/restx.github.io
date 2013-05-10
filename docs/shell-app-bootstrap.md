---
layout: docs
title:  "Bootstrapping a project with the shell"
---
# Bootstrapping a project with the shell

As you have seen in the [getting started](getting-started.html) section, it's super easy to bootstrap a new app with the shell.

Here is a little bit more information on that matter, especially on the questions asked. As the shell tells you you can for any question use a double question mark as answer to get more details on the question.

Here is the content of these help messages:
{% highlight console %}
restx> app new
Welcome to RESTX APP bootstrap!
This command will ask you a few questions to generate your brand new RESTX app.
For any question you can get help by answering '??' (without the quotes).

App name? ??
This is the name of the application you are creating.
It can contain spaces, it's used mainly for documentation and to provide default for other values.
Examples: Todo, Foo Bar, ...
App name? Todo
group id [todo]? ??
This is the identifier of the group or organization producing the application.
In the Maven world this is called a groupId, in Ivy it's called organization.
It MUST NOT contain spaces nor columns (':'), and is usually a reversed domain name.
Examples: io.restx, com.example, ...
group id [todo]?
artifact id [todo]? ??
This is the identifier of the app module.
In the Maven world this is called an artifactId, in Ivy it's called module.
It MUST NOT contain spaces nor columns (':'), and is usually a dash separated lower case word.
Examples: myapp, todo, foo-app, ...
artifact id [todo]?
main package [todo]? ??
This is the main package in which you will develop your application.
In Java convention it should start with a reversed domain name followed by the app name
but for applications (as opposed to APIs) we prefer to use a short name, like that app name.
It MUST follow Java package names restrictions, so MUST NOT contain spaces
Examples: myapp, com.example.todoapp, ...
main package [todo]?
version [0.1-SNAPSHOT]? ??
This is the name of the first version of the app you are targetting.
It's recommended to use Maven convention to suffix it with -SNAPSHOT if you plan to use Maven for your app
Examples: 0.1-SNAPSHOT, 1.0, ...
version [0.1-SNAPSHOT]?
generate ivy file [yes]? ??
Answer yes to get an Easyant compatible Ivy file generated for you.
If you don't know what dependency management is, answer yes, RESTX will help you with that matter.
If you know what you want, note that RESTX can also generate a Maven POM for you.
generate ivy file [yes]?
generate maven pom [no]? ??
Answer yes to get a Maven POM generated for you.
If you don't know what dependency management, use default answer.
If you know what you want, you probably shouldn't be reading this help message :).
generate maven pom [no]? yes
restx version [0.2.5-SNAPSHOT]?
signature key (to sign cookies) [7686162983702601318 bd91a655-beb4-4ca6-a053-1b4869bd35cd Todo todo]? ??
This is used as salt for signing stuff exchanged with the client.
Use something fancy or keep what is proposed by default, but make sure to not share that publicly.
signature key (to sign cookies) [7686162983702601318 bd91a655-beb4-4ca6-a053-1b4869bd35cd Todo todo]?
default port [8080]? ??
This is the default port used when using embedded version.
Usually Java web containers use 8080, it may be a good idea to use a different port to avoid
conflicts with another servlet container.
You can also use port 80 if you want to serve your API directly with the embedded server
and no reverse proxy in front of it. But beware that you may need admin privileges for that.
Examples: 8080, 8086, 8000, 80
default port [8080]?
base path [/api]? ??
This is the base API path on which RESTX will handle requests.
Being focused on REST API only, RESTX is usually shared with either static or dynamic
resources serving (HTML, CSS, JS, images, ...) and therefore is used to handle requests on
only a sub path of the web app.
If you plan to use it to serve requests from an API only domain (eg api.example.com)
you can use '' (empty string) for this path.
Examples: /api, /api/v2, /restx, ...
base path [/api]?
generate hello resource example [Y/n]? ??
This will generate an example resource with an associated spec test so that your boostrapped
application can be used as soon as it has been generated.
If this is the first app you generate with RESTX, it's probably a good idea to generate
this example resource.
If you already know RESTX by heart you shouldn't be reading this message anyway :)
generate hello resource example [Y/n]?
scaffolding app to `/Users/xavierhanin/Documents/tmp/todo` ...
generating module.ivy ...
generating pom.xml ...
generating hello resource ...
DONE - Your app should now be ready in todo
{% endhighlight %}
