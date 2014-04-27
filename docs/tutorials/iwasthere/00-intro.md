---
layout: tutorial-intro
tutorial: "I Was There"
title:  "Tutorial: I Was There"
---
This tutorial will help you develop the REST API of a web application called "I Was There". This application is used to let people tell the world they attended a particular event.

The final result can be see here: [http://iwasthere.restx.io/](http://iwasthere.restx.io/)

![I Was There Events Page](/images/tutorials/iwasthere/events-page.png)
![I Was There Event Page](/images/tutorials/iwasthere/event-page.png)


The tutorial won't focus on the client side, which is built using [AngularJS](https://angularjs.org) and [BootFlat](http://bootflat.github.io/).

Each step is illustrated with a commit on the github project of the tutorial: [https://github.com/xhanin/iwasthere](https://github.com/xhanin/iwasthere)

## Tutorial Steps

### [Create Project](01-create-project.html)

In this step you will create the project using restx shell `app new` command, and set it up in your IDE.

### [List Events](02-list-events.html)

This step will guide you to implement your first REST endpoint, used to get the list of events covered by the application.

### [Add Event](03-add-event.html)

In this step you will implement a REST endpoint to add events to the list.

### [Setup Database](04-db-setup.html)

In this step you will setup access to the MongoDB datastore, and use it to store the list of events instead of keeping them in memory.

### [First Spec Test](05-first-spec-test.html)

Here you will learn how to record a spec test based on your current endpoints implementation, and also how to use it as a JUnit test.

### [User signup](06-user-signup.html)

Here you will learn how to use MongoDB to store your application users, and add the endpoint to let users signup to use the application.

### [Attendee management](07-attendee-management.html)

In this step you will implement the endpoints used to add and return events attendees. You will also secure your endpoint so that regular users can only add themselves as attendee to an event, while an admin user can add anybody.

### [Add user specific data to Event object](08-user-specific-data.html)

You will learn how to add data to a domain object which is specific to the current user, and still make sure you don't persist this information in database.

### [Manage attendees messages](09-attendee-messages.html)

In this simple step you will complete the application features by providing a way to let attendee add messages for a particular Event.

### [Deploy application in the cloud](10-deploy-application.html)

Here you will learn how you can deploy the application in the cloud for free, using Heroku, GitHub Pages and MongoHQ.
