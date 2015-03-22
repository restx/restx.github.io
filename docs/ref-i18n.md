---
filename: ref-i18n.md
layout: docs
title:  "I18n"
---
# RESTX i18n support

RESTX has some support for i18n (internationalization), aimed to be used in a SPA (single page application).

## enabling i18n support

You need to add a dependency on `restx-i18n` to enable RESTX support for i18n.

You can do that with the shell:

```
restx deps add io.restx:restx-i18n:{{ site.restx-version }}
```

## RESTX Messages

RESTX i18n relies on a mechanism used to access internationalized messages accessed through a `Messages` interface.

A `Messages` is something very similar to a standard Java `ResourceBundle` (default implementation actually uses one underneath), so most of the documentation you can find for standard Java `ResourceBundle`, except that the files are encoded in `UTF-8` (as everything in RESTX).

## accessing Messages in RESTX app

When i18n is enabled your application benefits from a default `Messages` component that can be injected in any of your components.

Example:

{% highlight java %}
@Component
public class MyComponent {
    public MyComponent(Messages messages) {
        this.messages = messages;
    }
}
{% endhighlight %}

If you intend to use several `Messages` instances, name it when you ask for injection:

{% highlight java %}
@Component
public class MyComponent {
    public MyComponent(@Named("messages") Messages messages) {
        this.messages = messages;
    }
}
{% endhighlight %}


This instance loads its messages from a `labels` resource bundle at the root of your application classpath. So all you need to do to provide messages in this instance is to create a `labels.properties` file in your `src/main/resources` directory (if using default project layout). Then you can provide each locale using the `_XX` suffix as with standard resource bundles.

For instance:

{% highlight console %}
src/main/resources
  + labels.properties
  + labels_fr.properties
  + labels_de.properties
{% endhighlight %}

## accessing Messages from a REST client

by default the i18n module exposes the default `Messages` instance through a REST API.

This REST API is intented to be used by a SPA, and supports only basic operations.

It relies on the request locale to supply the messages. This means that it will provide the translations based on the standard HTTP `Accept-Language` header, and if not present it will use the default locale of the server.

You can access the default labels on `/i18n/labels.json` where you will get the key / messages in json format. 

You can also access them on `/i18n/labels.js` where you will get them in javascript so that you can load them using a `<script>` tag in your SPA. This is interesting because by default `<script>` loading is blocking, so you don't have to deal with an async interpolation of you keys / labels in your application.

The script served on this endpoint is similar to what is produced in json, except that it is decorated with a template to deal with it in javascript.

The default template is:

{% highlight javascript %}
// RESTX Labels - customize this with restx.i18n.labelsJsTemplate named String
window.labels = {LABELS};
{% endhighlight %}

As you can see it simply assigns the labels in a global variable named `labels`.

You can easily customize that by providing your own template as a named string in your RESTX app.

For instance in a module:

{% highlight java %}
@Provides @Named("restx.i18n.labelsJsTemplate")
public String labelsJsTemplte() {
    return "window.mylabels= {LABELS};";
}
{% endhighlight %}



## Message parameter interpolation

Another difference with standard Java resource bundle is that the `Messages` API supports a message parameter interpolation using mustache format rather than the standard Java format. This makes the message templates much easier to use on the client side, mustache having a very wide support, including very good support in Javascript.

Here is an example of use:

{% highlight java %}
messages.getMessage("some.msg.key", MessageParams.of("who", "World"), Locale.ENGLISH)
{% endhighlight %}

which with following `labels_en.properties`:

{% raw %}
some.msg.key=Hello {{who}}!
{% endraw %}

will produce `Hello World!`
