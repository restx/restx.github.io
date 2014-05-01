---
filename: ide-netbeans.md
title: Netbeans
layout: docs
---
# Setting up a restx project in Netbeans

<div class="note">
	<p>Instructions are provided here for only supported build tools Maven.</p>
	<p>Ivybeans plugin for netbeans is no more maintained.</p>
</div>

## Maven

To setup your RESTX project inside Netbeans with Maven support you will need to:

- create and configure the project for maven (choose pom in "generate module descriptor")
- open in Netbeans as a maven project.
- run the app using AppServer main class.

### Enable and configure annotation processing

  It seems that on netbeans 8.0 it is not possible to configure "compile on save" with the java 8 annotation processor.
By the way, a "build" action generate all the sources :

![RestX hello world open in Netbeans](/images/docs/netbeans-helloWorld.png)

<div class="go-next">
	<ul>
		<li><a href="ide.html"><i class="icon-cog"> </i> Setup your IDE</a></li>
		<li><a href="try-generated-app.html"><i class="icon-rocket"> </i> Try the generated app</a></li>
		<li><a href="generated-app-explained.html"><i class="icon-cogs"> </i> Understand generated app</a></li>
		<li><a href="getting-started.html"><i class="icon-play"> </i> Getting started</a></li>
		<li><a href="/community/"><i class="icon-beer"> </i> Community</a></li>
		<li><a href="/docs/"><i class="icon-book"> </i> Documentation</a></li>
	</ul>
</div>
