---

title: Simply applying "hasLayout"
slug: simply-applying-haslayout
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2006-03-05T00:00:00+00:00

draft: true

---

If you need to apply the [`hasLayout`][1] property to an element in Internet Explorer but don't want to add height or another potentially damaging <abbr title="Cascading Style Sheets">CSS</abbr> property, use the proprietry `zoom:1;`. It is an <abbr title="Internet Explorer">IE</abbr> only <abbr title="Cascading Style Sheets">CSS</abbr> property and sets the `hasLayout` flag to true while adding nothing visually or semantically to the element. Saved my skin more times than I care to remember.

[1]: http://www.satzansatz.de/cssd/onhavinglayout.html