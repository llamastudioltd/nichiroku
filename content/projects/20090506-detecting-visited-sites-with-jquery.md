---

title: Detecting visited sites with jQuery
slug: detecting-visited-sites-with-jquery
summary: An experiment to see how easy it is to inspect the browser history and see if a site has been visited.

date: 2009-05-06T00:00:00+00:00
location: London, UK

---

My recent adventure in writing a [jQuery plugin][1] led to me considering what other notionally unattainable client-side information could be gathered using a bit of Javascript and <abbr title="Cascading Style Sheets">CSS</abbr> manipulation. A bit of playing, (and a lot of understanding Safari's rather greedy method of storing styles) has resulted in my second [jQuery][2] plugin in as many months.


With the same disclaimers about elegance and infallibility, this plugin allows you to test a user's browser history against specific <abbr title="Universal Resource Location">URL</abbr>, returning a true/false value if they have visited the site in question.

    if ($.history.test('http://www.flickrshow.com')) {
      alert('You tasteful bugger.');
    }

Much like my previous effort, this plugin works by creating an <abbr title="Hyper Text Mark-up Language">HTML</abbr> element, in this case an `<a>` tag, and some associated <abbr title="Cascading Style Sheets">CSS</abbr> properties to alter the element in a measurable way. In this case, by adding some very specific styles to the `:visited` property of the link that can be measured in a fairly precise manner if the link has been visited in the past.

This isn't a bulletproof solution, however. You can only blindly test against the browser history, so need to make educated guesses and allow for changes in a <abbr title="Universal Resource Location">URL</abbr>, (such as trailing slashes or additional query string parameters). I've found that testing for one or two minor variations gives the best result – I might even add some minor intelligence to the function to account for this.

As before, the plug-in is of beta quality but seems to work in Safari 3, Firefox 3+, and <abbr title="Internet Explorer">IE</abbr> 6+. I've bundled everything together into a [GitHub repository][3], where you can also download version 1.0 of the plug-in in [uncompressed][4] and [compressed][5] form.

[1]: /projects/2009/04/22/detecting-installed-fonts-with-jquery/
[2]: http://www.jquery.com
[3]: https://github.com/beseku/jquery.history
[4]: https://github.com/beseku/jquery.history/blob/master/jquery.history.js
[5]: https://github.com/beseku/jquery.history/blob/master/jquery.history.mini.js
