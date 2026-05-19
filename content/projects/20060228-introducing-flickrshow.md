---

title: Introducing FlickrShow
slug: introducing-flickrshow
summary: A new javascript-based slideshow gallery for Flickr that can embedded in any website

date: 2006-02-28T00:00:00+00:00
location: London, UK

---

My [previous attempt][1] at gallery software was very popular and I still get requests for the original release even though it hasn't been updated since it was released. It wasn't, however, the solution I really wanted when I set out to make a [Flickr][2] driven slide show. My inspiration was and still is [Slideshow Pro][3] which I love for it's ease of use and the way you can just drop it into a page. I wanted a Javascript solution that would be as easy to use and provide a similar service.

## The Implementation

The result of my work is a centrally hosted slideshow that retrieves a photo-set from Flickr and displays the images in a horizontal slideshow format. It can be dropped into a page with just a line or two of script, can fit into any shape <abbr title="Hyper Text Mark-up Language">HTML</abbr> `DIV` and is completely skinable so users can link to their own style sheets if they dislike green. It is encapsulated as a Javascript object using a stripped down version of the excellent [prototype][4] library which should reduce any problems with other scripts on the page and ensure it is as compatible and extendable as possible.

## The Challenges

The biggest hurdle I encountered while creating a Javascript based solution was the inability of <abbr>AJAX</abbr> to make queries across domains, (a security feature that does make sense but is very frustrating). To overcome this problem I developed an interesting method of loading subsequent Javascript files using a combination of <abbr>PHP</abbr> and Javascript - the FlickrShow script writes new links to external Javascript files into the `HEAD` with query strings appended containing photo-set requests. [Flickarray][5] then retrieves the information from Flickr before sending a customised list of Javascript method calls back to the browser.

Other problems were more run-of-the mill. Getting the Javascript &lsquo;widget' to display properly across browsers is still an issue, (the IE 6 factor) and there is some inflexibility in the script which means you can currently only call one Flickrshow per page.

## Improvements

Apart from solving the issues mentioned above, I want to add a play/pause function to remove the need for constant clicking. I also want to retrieve more information on the current photograph, (tags, descriptions and notes) but there are issues with loading times at the moment.

If you want to have a play I've set up a mini site at [Flickrshow.com][6] which is running a demo complete with some stunning photography courtesy of [Limonada][7]. There is also a form to help generate the code required to install Flickrshow on your website.

[1]: /projects/2005/11/17/beseku-gallery-0-1/
[2]: http://www.flickr.com
[3]: http://www.slideshowpro.net
[4]: http://prototype.conio.net/
[5]: /projects/2009/07/31/accessing-flickr-hostip-info-with-php/
[6]: http://www.flickrshow.com
[7]: http://www.flickr.com/photos/limonada/