---
layout: default
title:  "Restx Stats Privacy Statement"
---
# RESTX Stats

Restx let you choose to collect and share stats on your application to give information to the RESTX community.

These statistics are helpful to hava a better idea on how RESTX is used, and therefore try to improve it in the right direction.

## Design

Collecting and sharing stats in RESTX has been designed with the following principles in mind:

### easy opt out

It is implemented in a separate module called `restx-stats-admin`, if you don't include it you don't get any stats collected, so it's purely optional.

So if you don't want to have stats in your restx application, simply make sure you have no dependency on the `restx-stats-admin` module.

### anonymous stats only

no information on the application name, the packages, ...

Here is how stats look like:

{% highlight javascript %}
{
  "timestamp": "2014-05-09T07:54:33.153Z",
  "appNameHash": "5b39c8b553c821e7cddc6da64b5bd2ee",
  "machineId": "f8873a71-cb5b-4a8d-a882-2974e8e20771",
  "port": 8080,
  "server": "Jetty 8.1.8.v20121106, embedded",
  "os": "Mac OS X, 10.9.2, x86_64",
  "java": "VM: Java HotSpot(TM) 64-Bit Server VM, 25.0-b70; Version: 1.8.0, 1.8.0-b132",
  "heapSize": 189792256,
  "restxVersion": "DEV-2014-05-09T09:53:57.823+02:00",
  "restxMode": "dev",
  "dataAccessInfo": "unknown",
  "totalUptime": 39964581,
  "currentUptime": 35330,
  "requestStats": {
    "GET": {
      "httpMethod": "GET",
      "requestsCount": 122,
      "minDuration": 1130,
      "maxDuration": 348766,
      "totalDuration": 1922298
    },
    "POST": {
      "httpMethod": "POST",
      "requestsCount": 1,
      "minDuration": 209904,
      "maxDuration": 209904,
      "totalDuration": 209904
    },
    "PUT": {
      "httpMethod": "PUT",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    },
    "DELETE": {
      "httpMethod": "DELETE",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    },
    "HEAD": {
      "httpMethod": "HEAD",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    },
    "OPTIONS": {
      "httpMethod": "OPTIONS",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    },
    "TRACE": {
      "httpMethod": "TRACE",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    },
    "CONNECT": {
      "httpMethod": "CONNECT",
      "requestsCount": 0,
      "minDuration": 999999999999999999,
      "maxDuration": 0,
      "totalDuration": 0
    }
  },
  "statsId": "5b39c8b553c821e7cddc6da64b5bd2ee--f8873a71-cb5b-4a8d-a882-2974e8e20771--8080--dev"
}
{% endhighlight %}

### minimal impact on performance

Collecting stats has a very low overhead, we have done load tests on a "realistic" application using MongoDB to access data, and the load test doesn't show any significant difference with and without stats collecting.

For the details, here are the results:

- [stats disabled](https://dl.dropboxusercontent.com/u/11351191/restx/gatling/iwasthere-stats-disabled-20140508144930/index.html)
- [stats enabled](https://dl.dropboxusercontent.com/u/11351191/restx/gatling/iwasthere-stats-enabled-20140508144035/index.html)

_Note that you shouldn't take these results as an indication of how RESTX performs. This load test was run with everything on a single box, without trying to reach the limits nor fine tune the test._

Moreover, the module does not starts any additional threads, it uses the request processing to collect stats, but also to save and share them.

On disk saving is only done once every 5 minute by default (and you can configure it), and sharing stats is only done once every 10 minutes by default (and you can configure it too).

Both of these are done in the request processing thread, but after the response has been returned, so it has no impact on the request processing time. It only affects the time taken to return the thread to the thread pool used for request processing.

### easy configuration

Easily configure if you want to store stats between run (so that it can also work on platforms where disk access is disabled), and if you want to share them (so that you can benefit from these stats only for you, and don't share them with the community).

Here are the keys you can use to configure the module:

`restx.stats.storage.enable`

enable or disable the storage of restx stats on the file system, allowing to gather statistics over multiple run

`restx.stats.storage.dir`

the directory in which stats should be stored

`restx.stats.storage.period`

the period, in ms, at which stats are saved to disk

`restx.stats.share.enable`

enable or disable the sharing of restx stats, allowing the community to collect statistics of RESTX usage. See http://restx.io/stats.html for details.

`restx.stats.share.url`

the URL on which stats should be shared (using a POST)

`restx.stats.share.period`

the period, in ms, at which stats are shared

### Open source

As the rest of RESTX, the stats module is open source, so you can have a look at the source code to know for yourself what it's doing.

The main classes are:

- the stats themselves called `RestxStats`,
- the stats collector, called `RestxStatsCollector`.
