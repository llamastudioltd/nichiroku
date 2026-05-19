---

title: FlickArray - Accessing Flickr with PHP
slug: flickarray-accessing-flickr-with-php
summary: A standalone PHP library for easily interacting with the Flickr API.

date: 2005-10-27T00:00:00+00:00

list: 
  home: false
  section: false

---

*This version, (and in fact FlickArray as a whole), has been discontinued in favour of the Flickr library written for CodeIgniter, discussed in more detail in [this article][1].*

Astute readers may have noticed the work going on at gallery.beseku.com. So far, these modifications are related to the user interface. I've been doing a lot of Javascript/<abbr title="Asynchronous Javascript and XML">Ajax</abbr> work at [Cimex][2] recently and the by-product has been a number of nice libraries that I want to make use of. I have also decided to plug the the whole thing into [Flickr][3] and although its not finished yet, I have finished work on a <abbr title="PHP: Hypertext Preprocessor">PHP</abbr> class to query the Flickr <abbr title="Application Programming Interface">API</abbr>.

The class is written in PHP 4.3 and uses REST to access the API. It is the first notable piece of object oriented programming I have done in PHP, (mostly spurred on by [Nick][4] and his comments on my poor procedural coding and use of global variables). It is written with my gallery software in mind, and so will most likely be missing features simply because they didn't have a place in the envisioned end product.

The class contains four externally accessible methods which you can use to retrieve your Flickr photograph information. These are 'fa_GetUserDetails', 'fa_GetTags', 'fa_GetAllImages’ and 'fa_GetImageDetails'. Each of these methods returns a formatted array containing the information sent back by Flickr. 

## Get User Details

This method retrieves extended user details for the user specified in the object declaration. You can call it using `$array = ($fa->fa_GetUserDetails());`, and it returns an array containing the following values:

    [real name] => Ben Sekulowicz
    [location] => London, UK
    [date] => 2002-01-01 00:00:00

## Get Tags

This method retrieves all of the tags that the specified user has created. You can call it using the following code:

    $array = ($fa->fa_GetTags());

It returns an array containing the following values:

    [0] => 2004
    [1] => boston
    [2] => chicago

## Get All Images

This method retrieves all of the images with the supplied tag (singular at the moment). 

    $array = ($fa->fa_GetAllImages("boston"));

It returns an array containing the following values:

    Array (
      [0] => Array (
        [id] => 6602973
        [url] => http://photos8.flickr.com/6602973_dd58a6e3a5
        [permission] => 1
        [title] => Harvard across the river
      )
      [1] => Array (
        [id] => 6602972
        [url] => http://photos8.flickr.com/6602972_7050a4ce98
        [permission] => 1
        [title] => Cheers
      )
    )

This method gets enough information from Flickr to display all images and their titles. The <abbr title="Universal Resource Location">URL</abbr> is built up from the image's server number, ID and 'secret’ number and is supplied missing a file extension so you can also [append a variable][5] to return the image in a number of sizes.

## Get Image

This method retrieves extended information for the image with the specified ID.

    $array = ($fa->fa_GetImage("6602973"));

It returns an array containing the following values:

    [author] => Ben Sekulowicz
    [date] => 2003-08-05 22:04:47
    [comments] => 0
    [tags] => usa boston 2004

I am in the middle of writing some wrapper functions that will transform the output to semantic <abbr title="eXtensible Hyper Text Markup Language">XHTML</abbr>, but these will most likely be specific to my gallery software. I also plan to add support for multiple tag searching and displaying comments, but at the moment the class is limited to what I need. <s>It is available here and is free to use and modify by all who want it</s>.

[1]: /blog/2009/07/31/accessing-flickr-hostip-info-with-php/
[2]: http://www.cimex.com
[3]: http://www.flickr.com
[4]: http://www.nickrigby.com
[5]: http://flickr.com/services/api/misc.urls.html

