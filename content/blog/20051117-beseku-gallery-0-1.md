---

title: Beseku Gallery 0.1
slug: beseku-gallery-0-1
summary: An AJAX-powered javascript library for displaying your Flickr photos on your own website.

date: 2005-11-17T00:00:00+00:00

list: 
  home: false
  section: false

---

A few weeks ago I (tentatively) released [flickArray][1], a simple <abbr title="PHP: Hypertext Pre-processor">PHP</abbr> class for retrieving image information from [Flickr][2]. While I love the idea of Flickr, I wanted to improve on the way the images were displayed on my site - this was the catalyst for creating both the flickArray class and a new user interface.

I've been experimenting with using javascript to add motion to a static <abbr title="eXtensible Hyper Text Mark-up Language">XHTML</abbr> interface for [Cimex][3] and the new gallery interface is an extension to that. The new gallery software consists of two parts; a back end - consisting of an updated and extended version of the original flickArray class together with a few wrapping <abbr title="PHP: Hypertext Preprocessor">PHP</abbr> pages, and a front end &lsquo;theme’ which uses <abbr title="eXtensible Hyper Text Mark-up Language">XHTML</abbr>/<abbr title="Cascading Style Sheets">CSS</abbr> to present the images and (if available) Javascript to enhance the interface and request additional images from Flickr without reloading the page or altering the documents semantic structure.

## The Back End

While the original flickArray class contained a number of useful functions, I needed to add to it in order to achieve some of the results I wanted. These changes mainly involved modifying the existing methods to retrieve additional data. I also created &lsquo;raw’ versions of all of the retrieval methods which return the information in pure <abbr title="eXtensible Mark-up Language">XML</abbr> form, a requirement for accessing the information through Flickr.

To make the retrieved information more usable, I also extended the flickArray class to add methods that returned the information in XHTML structures, (mainly lists) which can be accessed directly from a <abbr title="PHP: Hypertext Preprocessor">PHP</abbr>/<abbr title="eXtensible Hyper Text Mark-up Language">XHTML</abbr> page.

## The Front End

The interface was initially designed using <abbr title="eXtensible Hyper Text Mark-up Language">XHTML</abbr>/<abbr title="Cascading Style Sheets">CSS</abbr> to create a semantically structured page for displaying images. I loosely based the layout on [Todd Dominey][4]’s excellent [Slideshow Pro][5], which I feel is a brilliantly designed interface for viewing large amounts of images. Client side scripting is then used to alter the initial page to allow more images to be viewed without reloading the page. It is important to build web applications that can be used with or without Javascript, and so I wanted the scripting to enhance the gallery rather than comprise it. 

Script executed on page load determines the number of images to be displayed counting through the image links in the toolbar, and creates additional nodes in the &lsquo;images’ definition list for each one. This method means that the page loaded initially doesn't contain any superfluous or empty elements - the javascript adds them in only if the script is executed.

Once the elements have been generated and positioned, an onClick event is attached to each image link that will shift the relevant image into view and execute an <abbr title="Asynchronous Javascript and XML">AJAX</abbr> request to retrieve the image, image title and image description from Flickr via the flickArray class.

## Conclusions

I have been concerned over the use of <abbr title="Asynchronous Javascript and XML">AJAX</abbr> in recent months, as I felt that many people would implement it because they could, rather than for a specific and beneficial reason. I initially did not intend to use <abbr title="Asynchronous Javascript and XML">AJAX</abbr> on this project, but chose it because of the server requests it would save when used. Instead of reloading the page and thus rebuilding the flickArray object, only a single request is made to the server instead of three or four when a new image is selected. If you try using the system without javascript, it becomes much more tiresome to use because of the loading times involved.

The software still needs some improvements - I would like to enhance the interface further and the previous/next buttons are conspicuous by their absence. I also need to address how the system displays larger numbers of pictures, as currently the list of links simply wraps and looks confusing. Browser compatibility wise, there are some slight bugs in Opera that result in lost image descriptions.

## Release 0.1

A number of people have expressed interest in the software to display images on their own sites. You can download the entire gallery software under the [Creative Commons Attribution Non-Commercial][6] licence. If you are using it, please link to this article so other people can get the software too. I would also like to hear of any improvements so they can be added to the main code base. <s>Download Beseku gallery v0.1</s>.

 [1]: /blog/2005/10/27/flickarray-accessing-flickr-with-php/
 [2]: http://www.flickr.com
 [3]: http://www.cimex.com
 [4]: http://www.domineydesign.com
 [5]: http://www.slideshowpro.net
 [6]: http://creativecommons.org/licenses/by-nc/2.5/