---

title: Detecting installed fonts with jQuery
slug: detecting-installed-fonts-with-jquery
summary: An experiment to see how easy it is to test whether a particular font is installed and available to the web browser.

date: 2009-04-22T00:00:00+00:00
location: London, UK

---

I'm a massive fan of pushing the typographic capabilities of our current crop of web browsers and the supported <abbr title="Hyper Text Mark-up Language">HTML</abbr> and <abbr title="Cascading Style Sheets">CSS</abbr> standards. I'm not talking about embedded fonts or Flash/Javascript-based font generation but using simple <abbr title="Cascading Style Sheets">CSS</abbr> rules to bring nice fonts to the user, if available on their system. [Richard Rutter][1], [Guillermo Esteves][2] and myself have all published tutorials on how to include non-generic font families in your <abbr title="Cascading Style Sheets">CSS</abbr> declarations—the very same methods that allow me to use [Adobe Caslon Pro][3] on this website.

These methods are excellent for progressively enhancing the typography of a website, but are, (rightly so), based on providing a carefully selected set of fall-back fonts should the favoured family be unavailable. At present, there is no elegant way to determine whether your chosen font is being used and, if not, which of the numerous families in your font stack are instead.

Although I am loathe to call this solution elegant or fail-safe, I've tried to solve this problem by building a [jQuery][4] plug-in that should shed some light on which families your site is rendering in, and allow you to alter a site's behaviour, content or appearance accordingly. I've created a [demonstration page] that uses the plug-in to show which of the fonts you currently have installed and enabled out of a list that is fairly arbitrary, (the fonts currently active on computers around the [Outside Line][6] office).

The plug-in works by generating a paragraph of text, outside of the viewport, in a monospaced font. The paragraph is measured and re-rendered in the test font, (if available). If the paragraph dimensions change, then the rendered font must have too, and so the family must be installed/enabled.

    if ($.font.test("'ACaslonPro-Regular','Adobe Caslon Pro'")) {
      alert('You lucky bugger.');
    }

Usage of the plugin is fairly simple, returning a boolean true or false value when you pass in a <abbr title="Cascading Style Sheets">CSS</abbr>-style `font-family` declaration. You can also pass in, optionally, a `font-family` declaration that you know is different in dimensions and available to test against, should the defaults not work so well.

    $.font.test("'PanicSans','Panic Sans'", "Georgia, Times, serif");

The plug-in is of beta quality, and has only been tested to the extent of the fonts available to me. It works in Safari 3, Firefox 3+, and IE 6+. A lot will depend on the font names/post-script names/family names of the fonts you are testing for, as they tend to differ between vendors. In terms of example usage, aside from the [demonstration pages][7], <s>I've updated the about section of this site to deliver a more relevant message describing the design of the site</s>. You can download version 0.1 of the plug-in in [uncompressed][8] and [compressed][9] form.

[1]: http://clagnut.com/blog/2228/
[2]: http://blog.gesteves.com/post/36097597/helvetica-neue-light
[3]: http://www.fontshop.com/fonts/downloads/creative_alliance/adobe_caslon_pro_complete_vp/
[4]: http://www.jquery.com
[5]: https://github.com/beseku/jquery.font
[6]: http://www.outsideline.co.uk
[7]: https://github.com/beseku/jquery.font
[8]: https://github.com/beseku/jquery.font/blob/master/jquery.font.js
[9]: https://github.com/beseku/jquery.font/blob/master/jquery.font.mini.js