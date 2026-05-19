---

title: Safari and the first/last child
slug: safari-and-the-firstlast-child
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2007-04-10T00:00:00+00:00

draft: true

---

I don't often think to post tips on using <abbr title="Hyper Text Mark-up Language">HTML</abbr>/<abbr title="Cascading Style Sheets">CSS</abbr> anymore, partly because they are more than likely already out there and partly because it is such a stale and dull way of generating content on a website, (second only to posting 'best of’ lists). Sometimes though, the odd discovery warrants an entry, if only for personal reference.

Using pseudo selectors to generate content after elements, I noticed that Safari (2.0.4) would more often than not fail to generate content if a 'last-child’ rule was applied tp the element as well.

    ul li:after { content: " | " }
    ul li:last-child:after { content: "" }
    
The <abbr title="Cascading Style Sheets">CSS</abbr> above would quite often result in all of the list items losing their 'pipe'. However, if the code is changed to target the first child and apply the content before the element, the problem disappears.

    ul li:before { content: " | " }
    ul li:first-child:before { content: "" }
    
I have no idea why this happens, and no idea if this will be solved for the next release of Safari, (or even in the nightly builds), but it seems to solve an irritating little problem that pops up from time to time, (in the nav of this very site, for example).