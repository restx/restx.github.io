---
filename: samples.md
layout: docs
title:  "Samples"
---
# RESTX Samples and projects

Some samples are provided to demonstrate some of RESTX features.

Each sample is hosted in a separate github repo, so you can easily clone it or download its content.

We also list here open source projects using RESTX as they can be a good source of inspiration too.

<div class="note">
	<p>All samples can be imported in your IDE as described in <a href="ide.html">IDE support</a> documentation.</p>
</div>

## restx-samples-hello

This sample is the most basic, it's what is generated when you use the 'app new' command in the shell.
Check [Try generated app](try-generated-app.html) and [Understand generated app](generated-app-explained.html) page for details.

### Features demonstrated

- admin console
- api docs
- spec test
- spec as example
- servlet container integration

### Repo

[https://github.com/restx/restx-samples-hello](https://github.com/restx/restx-samples-hello)

## restx-samples-hellomongo

This sample is still pretty basic, compared to the `hello` sample it also demonstrates MongoDB integration.

The best way to learn how it is build is to look at the commits on github.

### Features demonstrated

- mongoDB integration with Jongo
- spec tests with Mongo Collections
- full CRUD

### Repo

[https://github.com/restx/restx-samples-hellomongo](https://github.com/restx/restx-samples-hellomongo)

## rxinvoice

This sample goes further than `restx-samples-hellomongo` to demonstrate restx with MongoDB integration in an invoice management app.

### Features demonstrated

- admin console
- api docs
- spec test
- spec as example
- mongoDB integration with Jongo
- spec tests with Mongo Collections
- full CRUD
- user management
- user rights

### Repo

[https://github.com/xhanin/rxinvoice](https://github.com/xhanin/rxinvoice)

## restx-samplest

This is a module of RESTX used both to demonstrate features and used as automatic tests for these features.
Therefore it contains a bunch of features demonstration, and not a full app sample.

### Features demonstrated

- many!

### Repo

[https://github.com/restx/restx/tree/master/restx-samplest](https://github.com/restx/restx/tree/master/restx-samplest)


## iwasthere

Tell the world you attended an event!

Sample used for [Xavier](https://github.com/xhanin)'s talk at Devoxx France 2014.

### Features demonstrated

- MongoDB integration
- MongoDB UserRepository
- Spec test
- AngularJS / Bootflat User interface
- Isolate Front-end from Backend using srv / ui project layout
- CORS

### Repo

[https://github.com/xhanin/iwasthere](https://github.com/xhanin/iwasthere)

## restx-singlejar

This is a variant of `restx-samples-hello`, but packaged as a single uber jar.

### Features demonstrated

- uberjar packaging
- simpleframework integration

### Repo

[https://github.com/xhanin/restx-singlejar](https://github.com/xhanin/restx-singlejar)


# Projects

List of open source projects using RESTX, which can be a good source of inspiration.


## Qzui

Qzui is an open source project based on RESTX and Quartz scheduler.

It's very basic, it's merely exposing a limited REST API and simple UI over Quartz Scheduler.

### Features demonstrated

- how to easily expose an existing library / component through a REST API
- Quartz integration through a module
- simple AngularJS UI

### Repo

[https://github.com/xhanin/qzui](https://github.com/xhanin/qzui)


## RTDM

Real Time Development Monitoring, tool used to follow the development workflow during a live coding talk.

### Features demonstrated

- MongoDB integration
- RabbitMQ integration
- using RabbitMQ to push events to browser using WebStomp and SockJS
- GitHub Hook integration
- AngularJS UI in a separate module

### Repo

[https://github.com/rtdm/rtdm-srv](https://github.com/rtdm/rtdm-srv)
[https://github.com/rtdm/rtdm-ui](https://github.com/rtdm/rtdm-ui)

## JMeter Reporting

Reporting tool for JMeter load tests.

### Features demonstrated

- MongoDB integration
- AngularJS / Bootstrap UI with nice graphics
- FileUpload support
- spec tests with MongoEmbed

### Repo

[https://github.com/lucaspouzac/jmeter-reporting](https://github.com/lucaspouzac/jmeter-reporting)


## zBlog

A simple blog engine.

### Features demonstrated

- Use vagrant / puppet to install MongoDB
- MongoDB integration
- spec tests

### Repo

[https://github.com/Zenika/zBlog](https://github.com/Zenika/zBlog)


## Remind It

Bookmark URLs and search over their content.

### Features demonstrated

- Basic Elastic Search integration
- AngularJs UI
- Vagrant to launch Elastic Search

### Repo

[https://github.com/ZenikaOuest/remindit](https://github.com/ZenikaOuest/remindit)


## Spatwork

Futsal oriented solution to count score at work.

### Features demonstrated

- MongoDB integration
- AngularJS / Bootstrap frontend
- spec tests

### Repo

[https://github.com/almorelle/spatwork](https://github.com/almorelle/spatwork)



## Hadoop On Demand restcloud

### Features demonstrated

- expose a CLI through a REST API
- making system calls through REST API

### Repo

[https://github.com/alcachi/hadoop-on-demand/tree/master/portal/REST/restcloud](https://github.com/alcachi/hadoop-on-demand/tree/master/portal/REST/restcloud)


## Your project?

Want to have your open source project featured here? Contact us on the google group or simply submit a pull request on this page!

# Attic

These samples are not actively maintained.

## restx-samples-beersample

This sample has been developed during the Couchbase workshop at BordeauxJUG. It demonstrates how to integrate RESTX with a CouchBase datastore.

_Note: Not maintained since restx 0.30_

### Features demonstrated

- couchbase as datastore

### Repo

[https://github.com/restx/restx-samples-beersample](https://github.com/restx/restx-samples-beersample)


## restx-samples-geektic

This sample is based on the code developed during [CodeStory](http://code-story.net/) at [Devoxx France](http://devoxx.fr) 2013.

This sample demonstrates not only a REST API but also the client with a nice UI.

_Note that this sample is not actively maintained_

### Features demonstrated

- mongoDB integration with Jongo
- using RESTX to serve static assets
- custom routes, without annotations
- servletless server
- integrating a RESTX server to perform Selenium tests, based on FluentLenium / GhostDriver / PhantomJS
- AngularJS front end, LESS stylesheets, coffescript controllers

### Repo

[https://github.com/restx/restx-samples-geektic](https://github.com/restx/restx-samples-geektic)
