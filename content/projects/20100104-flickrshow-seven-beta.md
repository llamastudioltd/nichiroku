---

title: Flickrshow Seven
slug: flickrshow-seven-beta
summary: The seventh version of my popular javascript slideshow library, now fully native and a fraction of the size.

date: 2010-01-04T00:00:00+00:00
location: Tokyo, Japan

list: 
  home: false
  section: false

---

By far the most popular of any of my personal projects is [Flickrshow][1], a Javascript slideshow that evolved from earlier [gallery projects][2] into the first public version in [2006][3]. For those unfamiliar with the project, the goal is to allow as many people as possible to embed a slideshow displaying [Flickr][4] images into a webpage. The emphasis has always been on simplicity and ease of use, rather than complex features, and this has led to its use by scores of people who most likely would have resorted to poorer implementations or worse, none at all.

After a hiatus of over a year, I recently released the newest version of Flickrshow to public beta testing. The previous version had no real faults, other than a few glaring feature omissions, but was definitely showing its age. The goal of this new version was to add a few of the most requested features and, more importantly, remove another level of complexity to the implementation by removing any framework dependance from the slideshow, (it was previously using the Prototype framework).

This version of Flickrshow uses only native Javascript functions, and contains its own animation and remote loading functionality. It now features auto-play, configurable pop-up controls, better themes, multiple shows per page and [improved integration][5] with Flickr. It is also compatible with all modern browsers, (although by making use of certain CSS properties it will look slightly less rounded and transparent in older software) and the size of the script has been reduced from 58Kb to 8kb. If you are interested in the project, please [try out the new version][6] and [register any issues][7].

[1]: http://www.flickrshow.com
[2]: /projects/2005/11/17/beseku-gallery-0-1/
[3]: /projects/2006/02/28/introducing-flickrshow/
[4]: http://www.flickr.com
[5]: /projects/2009/07/31/accessing-flickr-hostip-info-with-php/
[6]: http://api.flickrshow.com/v7/
[7]: http://twitter.com/beseku