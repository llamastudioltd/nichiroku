---

title: Hacking Your CSS
slug: hacking-your-css

date: 2005-02-22T00:00:00+00:00
draft: true

---

I know I have made my feelings about browser hacking [quite clear][1], but I do have to use workarounds on client facing sites. Organising your hacks or workarounds so they make sense is a tough task, and I thought I would share how I order my hacks for ease of use. I prefer the route of seperating each browser to be hacked into it's own stylesheet, because then you can order them so each rule is applied in the same order, which is far easier to read and work with.

I start with a root stylesheet imported so only version 4+ browsers can use it. This file itself imports a <abbr title="Cascading Style Sheet">CSS</abbr> file for Windows <abbr title="Internet Explorer">IE</abbr> browsers and a <abbr title="Cascading Style Sheet">CSS</abbr> file for Macintosh <abbr title="Internet Explorer">IE</abbr>, plus the generic styles that all good browsers can use. This method is the same as that used by John Serris at [Phono Phunk][2], (nice site as well), and uses various filters to only show styles to the different families.

    /* Actual styles for nice browsers */
    @import "layout.css";
    @import "text.css";
    /* Import list IE Win family */
    /*\*/ @import "hacks-ie-win.css"; /**/
    /* Import styles for IE Mac */
    /*\*//*/ @import "hacks-ie-mac.css"; /**/

For <abbr title="Internet Explorer">IE</abbr> on OS X, this is the end of it, and the rules in this style sheet should be seen by no other browsers. For <abbr title="Internet Explorer">IE</abbr> on Windows, I then import three style sheets for <abbr title="Internet Explorer">IE</abbr> 5, 5.5 and 6 respectively using the `hacks-ie-win.css` file. These <abbr title="Cascading Style Sheet">CSS</abbr> files will also be seen by some good browsers, so the rules they contain have to use the [* html hack][3] to apply them to <abbr title="Internet Explorer">IE</abbr> only. The method used to import the <abbr title="Internet Explorer">IE</abbr> 6 sheet would also show it to <abbr title="Internet Explorer">IE</abbr> on OS X, but that browser won't see this page because it won't see the `hacks-ie-win.css` file.
    
    /* Import only for IE 6 */
    @import "null?"\{";
    @import "win/ie-6.css";
    @import "null?"\}";
    /* Import only for IE 55 */
    @media tty {
    i{content:"";/*" "*/}}@m;
    @import 'win/ie-55.css'; /*";}
    }/* */
    /* Import only for IE 5 */
    @media tty {
    i{content:"";/*" "*/}};
    @import 'win/ie-5.css'; {;}/*";}
    }/* */

Thats a total of six files and a sub-folder, which is a lot of extra weight, but in past projects I have hacked out about 50% of the original rules for poor browsers, and this saves a lot of confusion when working on a large site. Just as a disclaimer, this post doesn't at all change my stance on using hacks. It is possible to design sites that don't require hacks on the majority of platforms, (most of my designs are made to work on <abbr title="Internet Explorer">IE</abbr>6 as well as modern browsers with no workarounds), but occasionally you do need to, and this is my way of doing so.

[1]: /blog/2005/01/26/have-you-seen-this-site-in-ie-5/
[2]: http://phonophunk.phreakin.com/news/?p=46
[3]: http://www.dithered.com/css_filters/css_only/star_html.html