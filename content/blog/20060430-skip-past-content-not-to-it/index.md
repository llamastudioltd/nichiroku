---

title: Skip past content, not to it
slug: skip-past-content-not-to-it
summary: Why ordering and structuring your markup correctly improves the accessibility of your content.

date: 2006-04-30T12:00:00+00:00

---

_This is a reproduction of an article written for the inaugural [Cimex][1] magazine in July 2006._

The separation of a web site into structural, presentational and behavioural layers is the key to making a usable, accessible and future proof web site, and the fact that <abbr title="Cascading Style Sheets">CSS</abbr> and unobtrusive Javascript allow us as developers to do this has been a major factor in the uptake of web standards. The reason this separation is so important lies in how it allows so many devices to access your data in so many ways. Mobile phones see a different version of your site to Safari, which sees a different version to JAWS yet all access the same mark-up and the same <abbr title="Universal Resource Location">URL</abbr>. Maintaining this separation intelligently is the key to allowing as many users as possible to access to your data using any means they want.

Many web developers are still falling quite short of this separation, not because they are using tables for layout, inline styling or obtrusive javascript but because they are ordering their mark-up not by how it is used but how they want it to appear. The structural layer of a web site should focus on enriching your content semantically to provide a user with the content they need in the most accessible way possible. This doesn't just mean using suitable heading hierarchies, lists and labels but also ordering your content properly to provide suitable focus to the most important parts of the page.

Users who visit sites with devices that support limited or no <abbr>CSS</abbr>, or with devices that do not display your content visually will not see your content in the organised columns and colours that the majority do – they will be browsing your site in a single column ordered as your mark-up is. This often means they first receive a long list of nav items, logos and introductory paragraphs when what they really want is the latest article, train time or number of goals Thierry has scored today.

There seems to be a growing trend for developers to include 'skip to content’ links as a solution to this problem. These links bypass the nav and header elements and move the user straight to the content, but users still have to move around a page instead of being served what they want straight away. This technique also fails to account for other ways in which your data is accessed; search engines indexing your pages may rank prevalent content more highly for example, and they won't use skip links to pursue the content you deem most important on the page. Although I am not an <abbr title="Search Engine Optimisation">SEO</abbr> expert I can't believe that important, relevant elements at the top of a page won't have more influence on a search engine in how it interprets the meaning of your site.

There are plenty of <abbr>CSS</abbr> techniques that can be used to separate your page structure from appearance—the excellent methods explained at [Position Is Everything][2] for creating columns in any order on the canvas, for example. Just remember that the most important column is the one containing what the users came for.

[1]: http://www.cimex.com/
[2]: http://www.positioniseverything.net/articles/onetruelayout/