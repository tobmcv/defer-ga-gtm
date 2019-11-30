# Defer Google Analytics and Tag Manager

How to defer loading Google Analytics and Google Tag Manager JS

**Why should you defer loading these services?** 

There are many benefits to deferring javascript. In brief, it makes users happy because your website will load faster, and it can also make you money.

**The first reason** we want to defer javascript is for performance.

Deferring scripts that are not required for rendering a page will allow the page to load faster and become interactive sooner for the user. Regardless of how much javascript your application contains, each script adds up over time and effects the perception of your application. This applies to any javascript run in a browser.

Research and user feedback continually show that what they prioritise is good User Experience (UX) in the form of design and speed. Your design should be simple and the app should be fast. 

**The second reason** you want this is because of the benefits that are related to speed.

In a business setting a website that is compliant with web standards and loads faster in a browser will be prioritised in search engines such as Google, Bing and Yahoo. This can give you more traffic which is valuable regardless if you are a startup or an established business. 

From the user point of view, a good experience is the most likely reason they will enjoy using the application and return. This obviously applies to websites that care about ecommerce KPIs as well as every other category imaginable: banking, news publishers, video, music and game streaming, chat and social media services and public information providers in local and federal government.

There simply is no service that someone wants to wait in line for. In every case I've done this for a client it has had a positive impact on user satisfaction and in some cases we saw increased revenue that correlated with faster page load speeds.

In my experience developers will appreciate working on a good user experience and the challenge of incremental gains, and this particular recommendation for Google services is a quick win you can validate using your server logs or real user monitoring for page speed.

To summarise, you are improving the service for everyone, users and developers alike.

**What does defer mean?**

Deferring javascript means that we are literally lowering the priority for the browser to run our javascript.

This does not mean that it won't load, but the browser will prioritise running any other HTML and Javascript that is synchronous and asynchronous. Deferred javascript is the last set of components of your website that will be loaded. 

So any javascript that your app needs to run, f.ex javascript that loads information from a user on a logged in page, should be loaded either synchronously or asynchronously.

Telemetry and analytics software such as Google Tag Manager and Google Analytics however is not required for the page to run, and can be given a lower priority.

**How is defer different from async JS?**

Read this excellent explanation by Flavio for a full explanation: [Efficiently load JavaScript with defer and async](https://flaviocopes.com/javascript-async-defer/)

My short summary of the 3 ways to load JS in the browser

| Javascript tag type | Example | Description |
| :-------------- | :------: | :----------- |
| Synchronous | `<script src="script.js"></script>` | The browser will download and execute this javascript immediately, blocking all other requests |
| Asynchronous | `<script async src="script.js"></script>` | The browser will download and execute this javascript while attempting to load other assets of HTML and Javascript, and sometimes block other requests in the process |
| Defer | `<script defer src="script.js"></script>` | The browser will finish downloading and executing HTML and javascript that is not deferred, and after the DOM interactive event fires it will execute the deferred javascript |

**So why not just run this async like Google recommends?**

Because async JS can interfere with other async and synchronous JS, which you are already using to load user data on logged-in pages, large media files and most importantly the content itself - which is what the user came to your app for in the first place.

More importantly, Google developers do not recommend running this asynchronously. In their own Web Fundamentals series they recommend deferring javascript: [Loading Third-Party JavaScript](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript).

**Are there any risks?**

I know only one risk: Very slow apps with bad performance.

For every employer I have ever worked with, and every client I've ever held, only one had a problem with deferring javascript: The company with a very slow checkout page on their online store. It could take anywhere between 5-20 seconds for this page to load before sending the user to the receipt page.

If your app has a page that loads slowly, f.ex in the range of over 5 to 12 seconds, you might see that deferred javascript doesn't run in time before the user moves to the next page.

In that case, the deferred javascript won't have time to run and you might miss something. If you defer GTM or GA or both you might lose tracking for pageviews and transactions.

**My app is slow. What do I do?**

Work on your website performance and speed. Instead of rendering tons of javascript in the user's browser, consider pre-rendering it, compiling in advance into a static page or just work on your app architecture to speed up your javascript.

If you are requesting even 2 or 3 scripts from an external host please consider hosting them yourself. This will almost certainly also give you a performance boost.

I recommend reading and working your way through the Web Fundamentals series from Google Developers. Some developers swear by setting a performance budget to set a goal and start identifying opportunities to reduce page load times. This tip from me on GTM, GA and GTAG is just one of those low-hanging fruits. Good luck.

I also recommend the Mozilla Developer Network series

- [Web Performance](https://developer.mozilla.org/en-US/docs/Learn/Performance)