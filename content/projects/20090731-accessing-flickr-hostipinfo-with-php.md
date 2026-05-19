---

title: Accessing Flickr & HostIp.info with PHP
slug: accessing-flickr-hostip-info-with-php
summary: A Codeigniter-compatible library for easily interacting with the Flickr and Host IP APIs. 

date: 2009-07-31T00:00:00+00:00
location: London, UK

---

Recently, we at [Outside Line][1] launched a new website for Golden Wonder's new noodle brand, [The Nations Best][2]. In a departure from the normal day-to-day, I built the bespoke server-side functionality to power the nifty Flash front-end. In doing so, I put together a few <abbr title="PHP: Hypertext Pre-Processor">PHP</abbr> libraries, one to access the [Flickr][3] <abbr title="Application programming Interface">API</abbr> and one to access the [Host IP][4] geolocation service <abbr title="Application programming Interface">API</abbr>.

    <?php
      $this->load->library('flickr');
      $this->flickr->set_cache_duration(3600);
      $this->flickr->set_cache_location('cache/flickr/');
      $images = $this->flickr->get('flickr.photos.search', array(
        'per_page' => '50',
        ’sort' => 'relevance',
        'text' => 'Exmouth Market',
      ));
    ?>

Both classes, being built at the same time, have a similar structure and similar functionality. They both feature a cache mechanism to limit your requests and enhance performance, and the both are pretty open ended in what they allow you to do. The Flickr class allows access to any method that doesn't require authentication, and returns the results as a <abbr title="PHP: Hypertext Pre-Processor">PHP</abbr> array, (in the same format as the original Flickr response).

    <?php
      $this->load->library('hostip');
      $this->hostip->set_cache_duration(3600);
      $this->hostip->set_cache_location('cache/hostip/');
      $latlong = $this->hostip->getLatLong('173.45.226.6');
      $location = $this->hostip->getLocation'173.45.226.6');
    ?>

The Host IP class is slightly more limited, but is easy to extend if more information is required. The results are obtained form a parsed <abbr title="extensible Markup Language">XML</abbr> response, and contain information outside of the latitude, longitude, city and country. Because of the way in which SimpleXML handles the name spaces, there is also bit of hacking in place to parse the <abbr title="extensible Markup Language">XML</abbr>.

You can download the [Flickr][5] and [Host IP][6] classes from my GitHub account, and they are both offered freely but with no support or guarantee.

 [1]: http://www.outsideline.com
 [2]: http://www.thenationsbest.co.uk
 [3]: http://www.flickr.com
 [4]: http://www.hostip.info/
 [5]: https://github.com/beseku/php.flickr
 [6]: https://github.com/beseku/php.hostip