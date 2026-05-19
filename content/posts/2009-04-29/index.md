---

title: "Exploding the myths of web design: Only use web fonts"
summary: Why it is easier than you think to enhance your designs by using the fonts installed on your users computer.

date: 2009-04-29T12:00:00+00:00
location: London, UK

---

_This is a reproduction of a boxout written for the "Exploding the myths of web design" feature in [.Net magazine, issue 189][1]._

Have you ever been handed a design for a website and wondered what font the designer has used for the body copy? Because I can honestly say I never have, and this certainly isn't down to web designers having a love for Georgia and Arial. Instead, it's down to a common misconception that the only fonts that can be rendered in a browser are the old 'favourites'. The thing is, a modern web browser is perfectly capable of rendering any font that a user has installed, and because of the popularity of particular software packages, the list of relatively commonplace fonts includes some beauties.

On [24 Ways][2], [Richard Rutter][3] showed that if you take into account fonts installed by Windows and Mac OS X along with those from Microsoft Office and Adobe's Creative Suite, the resulting list includes some rather lovely serif and san-serif fonts that a designer can use to bolster their designs. With some carefully selected fall-backs, there's no reason why a good developer can't provide users with Caslon or Jenson in place of Georgia, or Helvetica Neue in place of Arial. By using the <abbr title="Cascading Style Sheets">CSS</abbr> `font-weight` property, you can even use differing weights to further enhance your work.

Most websites are launched to a specific audience or demographic, and if they aren't then your marketing team is missing a trick. If you have a good idea who will be looking at your site, it's then easy to treat them to some nicer typography. For example, [Panic][4] achieves this on the company's website for FTP client [Coda][5] by using Helvetica Neue Light, after surmising that the majority of visitors will be Mac OS X users, who have the font installed on their system by default. Even if you don't have such a targeted audience, you can still play the percentage game, and in doing so, you can at least treat a portion of your visitors to a more refined, unique look. Call it typographic progressive enhancement!

[1]: http://www.netmag.co.uk/zine/latest-issue/issue-189
[2]: http://24ways.org
[3]: http://24ways.org/2007/increase-your-font-stacks-with-font-matrix
[4]: http://www.panic.com
[5]: http://www.panic.com/coda