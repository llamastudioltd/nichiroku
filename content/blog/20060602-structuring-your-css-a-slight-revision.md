---

title: Structuring your CSS - A Slight Revision
slug: structuring-your-css-a-slight-revision
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2006-06-02T00:00:00+00:00

draft: true

---

With the forthcoming release of a new version of Internet Explorer, many of the hacks and workarounds used by site developers to target individual browser flaws and serve custom <abbr title="Cascading Style Sheets">CSS</abbr> are going to stop working. The developers of <abbr title="Internet Explorer">IE</abbr> 7 have themselves warned that a number of the hacks, (such as those discussed previously on this site) will no longer work and should be avoided. They're suggestion as a replacement method is to use conditional comments, something we have been implementing at [Cimex][1] for some time.

The following is an example in using conditional comments to serve <acronym>CSS</acronym> files to different versions of Internet Explorer. One caveat is that Internet Explorer 5 (<abbr title="Macintosh Operating System Ten">OS X</abbr>) does not make use of these conditonal comments and, if you are still supporting it, will need to be served <abbr>CSS</abbr> using an alternative method.

    <link rel="stylesheet" ... href="list.css" />
    <!--[if IE 5]>
    <link rel="stylesheet" ... href="ie-5-win.css" />
    <![endif]-->
    <!--[if IE 6]>
    <link rel="stylesheet" ... href="ie-6-win.css" />
    <![endif]-->
    <!--[if IE 7]>
    <link rel="stylesheet" ... href="ie-7-win.css" />
    <![endif]-->

The above code provides a default &ldquo;list.css&rdquo; stylesheet which in my template serves a stylesheet to reset all elements to their default values and a stylesheet for the site itself. Conditional comments supplement this with a specific <acronym>CSS</acronym> file for each browser version under Microsoft Windows. The <abbr title="Macintosh Operating System Ten">OS X</abbr> version is served its <acronym>CSS</acronym> file from within the &ldquo;list.css&rdquo; file.

This method has worked for my testing of the preview of <acronym>IE</acronym> 7 beta 2. That doesn't mean it will work in the final version.

[1]: http://www.cimex.com
