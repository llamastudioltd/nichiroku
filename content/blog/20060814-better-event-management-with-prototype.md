---

title: Better event management with Prototype
slug: better-event-management-with-prototype
summary: Examining how the Prototype library handles events and event listeners, and how I use it in my code

date: 2006-08-14T00:00:00+00:00

---

Of all of the frameworks currently available for the rejuvenated Javascript language [Prototype][1] is the most popular. The developer, [Sam Stephenson][2] has now been employed by [37Signals][3] and has been working on integrating his framework and its spinoff effects library [Scriptaculous][4] with [Ruby on Rails][5], the massively popular new server side language. So its going to be around for a while. 

One of the most useful features of the framework is how it allows you to easily build classes to encapsulate your code and prevent it from interfering with existing or future code. We have used it extensively at [Cimex][6] with some projects making use of three or four different classes, all running independently of each other while addressing the same DOM tree. However the implementation of events and event listeners with Prototype can seem a bit convoluted and unless you have been there before and know the tricks of the trade, can be very frustrating.

As a quick recap on creating objects with Prototype, and as a way to start building an example, consider the following code. I've created a new class called <code class="inline">Popups</code> and its constructor function, (which is always called <code class="inline">Initialize</code> - how American). Notice how I have set internal variables, (properties) using the <code class="inline">this</code> keyword - its an important part of developing classes in any language to be able to self-reference a class to call internal variables and methods or functions.

    var Popups = Class.create();
      Popups.prototype = {
        initialize: function() {
        this.popupCount = 0;
      }
    }

Now I can add another method, (function) to my class and reference it using the <code class="inline">this</code> keyword in the same way. I also want to be able to call this method on the occurrence of a particular event, such as clicking a link. It is important to be aware of a number of things when doing this. The first is that an item can observe the occurrence of more than one event if implemented correctly. The second is that I want to preserve the <code class="inline">this</code> keyword so that it relates to the class and not the element that observes the event, but also still be able to access the element.

    var Popups = Class.create();
      Popups.prototype = {
      initialize: function() {
        this.popupCount = 0;
        Event.observe($("clickMe"), "click",  this.onClickTalk.bindAsEventListener(this));
        Event.observe($("clickMe"), "click", this.onClickPink.bindAsEventListener(this));
      },
      onClickTalk: function (e) {
        this.popupCount ++;
        alert&#40;"You clicked the link " + this.popupCount + " times!"&#41;;
      },
      onClickPink: function (e) {
        Event.element(e).style.color = "#C09";
      }
    }

The code above illustrates almost exactly how we should be observing events with Prototype. We use the <code class="inline">Event.observe</code> method to get an element to observe the occurrence of an event. We then bind the parent class to the occurrence of the event with <code class="inline">bindAsEventListener(this)</code> so we can still access variables within the class. Notice how we can also assign multiple methods to the same event. You can also see from the example above how to reference the trigger element, (in this case an element with an ID of <code class="inline">clickme</code>) using the <code class="inline">Event.element(e)</code> method. 

    initialize: function() {
      this.popupCount = 0;
      Event.observe($("clickMe"), "click", this.onClickTalk.bindAsEventListener(this));
      Event.observe($("clickMe"), "click", this.onClickPink.bindAsEventListener(this));
      $("clickMe").onclick = function() { return false; }
    }

As usual, browser bugs mean this isn't the final code, and as is often the case the solution is to mess with our nice clean code. In this case, some browsers, (such as Safari) do not understand the Prototype method to stop the event after we have executed our code - the only way to guarantee that the original element event will not occur, (in this case the browser following the link to its <abbr title="Unversal Resource Location">URL</abbr>), is to add an old style <code class="inline">.onclick</code> after you have attached the <code class="inline">Event.observe</code> methods to your element.

Apologies for the awkward and technical article, but this was something I spent a long time solving for [Flickrshow][7] and now I have a solution I thought others might want it too.

[1]: http://prototype.conio.net/
[2]: http://conio.net/
[3]: http://www.37signals.com/
[4]: http://script.aculo.us/
[5]: http://www.rubyonrails.com
[6]: http://www.cimex.com
[7]: http://www.flickrshow.com