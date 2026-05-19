---

title: Extending Codeigniter for REST
slug: extending-codeigniter-for-rest
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2009-08-04T00:55:00+00:00

draft: true

---

I've recently been developing a little something in [CodeIgniter][1] that features an <abbr title="Application Programming Interface">API</abbr> that is as true as possible to the principles of <abbr title="Representational State Transfer">REST</abbr>. In order to do this, I had to extend the core CodeIgniter Input library to allow access to properly escaped values from DELETE or PUT input in the same way as you would normally access GET/POST input.

    <?php
      function delete($index = '', $xss_clean = FALSE) {
        if (strtoupper($this->server('REQUEST_METHOD')) != 'DELETE') {
          return FALSE;
        }
        parse_str(file_get_contents&#40;"php://input"&#41;, $_DELETE);
        return $this->_fetch_from_array($_DELETE, $index, $xss_clean);
      }
    ?>
    
The code is pretty simple, and unfortunately does require `file_get_contents` until I can figure out an alternative way of accessing the input. The whole class can be downloaded, played with and forked from my [GitHub account][2].

[1]: http://www.codeigniter.com
[2]: https://gitlab.com/beseku/CodeIgniter.RESTFulDemo
	