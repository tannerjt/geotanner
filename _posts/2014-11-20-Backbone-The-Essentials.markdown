---
layout: post
title: "Backbone: The Essentials"
categories: javascript frameworks backbone
tags: javascript frameworks backbone
---
**What is Backbone.js?**

[Backbone.js][backbone] is a JavaScript library that provides a simplistic structure to organize your client-side JavaScript code.  If you have used other popular frameworks, like [AngularJS][angular], you will have an easier time getting familiar with [backbone.js][backbone].  For those coming from a traditional MVC (model-view-controller) framework, you may be a little confused with the lack of a controller in [backbone.js][backbone].  In [backbone.js][backbone], your application logic can be built with your view.  The popular term for these types of frameworks is MV\*.

There are plenty of great resources for learning [backbone.js][backbone].  I would reccommend [Addy Osmani's][addy] eBook on developing and understanding [backbone.js][backbone] - [here][fundamentals].

This posting is meant to be a general overview of the very key components in [backbone.js][backbone].  Hopefully it will give you that 'A-Ha' moment before you dive in too deep. 

**Basic Components**

* [Model][model] - data and data logic
* [View][view] - interface and interaction logic

There are plenty of other important concepts, but lets just start with the basics.

**The Model**

Your [model][model] can be simply defined as a way to define your data within [backbone][backbone].  You extend *Backbone.Model*, and define it's instance properties.  Your resulting [model][model] is a constructor function that can be instantiated by calling it.  Let's create a simple example of creating a simple *State* model.

{% highlight javascript %}
// Extend Backbone.model
var StateModel = Backbone.Model.extend({});

// Create an instance of our StateModel
var statemodel = new StateModel({
    name : "Oregon",
    capital : "Salem"
});
{% endhighlight %}

**The View**

The [view][view] lets you define your interface, user interactions, and custom events.  If you pass in a model when you instantiate your view, you can provide logic for how your view updates when your model's data changes.  Lets create a basic view that updates when the State name changes.  Let's also use underscores template method to return the html.

{% highlight javascript %}
// Extend Backbone.View
var StatesView = Backbone.View.extend({
    events : {
        "click button" : "changeState",
    },
    template : _.template("<h2><%= name %></h2><button>Change</button>"),
    initialize : function () {
        // update view when model changes
        this.model.on('change', this.render, this);
    },
    render : function () {
        this.$el.html(this.template(this.model.toJSON()));
        return this;
    },
    changeState : function () {
        this.model.set("name", "South Carolina");
    }
 });

// Create an instance of our StatesView
var statesview = new StatesView({model:statemodel});
{% endhighlight %}

Lastly, lets render the html and push the element to the DOM.

{% highlight javascript %}
$("#states").html(statesview.render().el);
{% endhighlight %}

**Resources**

* Working Example - [in JSFiddle](http://jsfiddle.net/hhsgg80o/)
* EBook - [By Addy Osmani][fundamentals]
* Small Example on GitHub - [Example](https://github.com/tannerjt/backbone_example)

**Whats Next?**

This example is incredibly basic, but that was the intention.  It shows a small working example of the model and view working together.  There are a few basic events, one on the model and another in the view.  I would reccommend [Addy Osnami's][fundamentals] book or reading the documentation on [backbone.js][backbone].  My [GitHub Example](https://github.com/tannerjt/backbone_example) expands into using [collections][collection], which you will learn later.  The key thing is to keep building and experimenting with the library until you don't need to look at the documentation.  Happy Coding!


[backbone]: http://backbonejs.org/
[underscore]: http://underscorejs.org/
[angular]: https://angularjs.org/
[addy]: http://addyosmani.com/blog/
[fundamentals]: http://addyosmani.github.io/backbone-fundamentals/
[model]: http://backbonejs.org/#Model
[collection]: http://backbonejs.org/#Collection
[view]: http://backbonejs.org/#View
[router]: http://backbonejs.org/#Router
