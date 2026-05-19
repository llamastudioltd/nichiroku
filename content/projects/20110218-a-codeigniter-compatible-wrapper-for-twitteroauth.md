---

title: A CodeIgniter-compatible wrapper for Twitter OAuth
slug: a-codeigniter-compatible-wrapper-for-twitteroauth
summary: A clean way of authorising users with Twitter's new OAUth system when using CodeIgniter

date: 2011-02-18T00:00:00+00:00
location: Tokyo, Japan

---

As part of a new [iA][1] project, we needed a clean way of authorising a user via [Twitter's][2] new OAuth system. Not wanting to reinvent the wheel, I hunted for a good library and found [TwitterOAuth][3], by [Abraham Williams](http://abrah.am/). Unfortunately the library was structured in a way that made it difficult to use with the [CodeIgniter][4] framework, and left a lot to the developer when trying to initially authenticate a user. In working with the code I developed a simple wrapper library that solves these issues and makes Twitter even more easy to work with from CodeIgniter 2.0.

The only major non-structural change is a new authentication method that deals with the fetching and management of the `oauth token` and `oauth token secret` variables between redirects. Implementing it is as simple as including the following code within a controller method. When the method is accessed, it will redirect to Twitter to authenticate and return to the controller when successful.

    public function sign_in() {
      $this->load->library('twitter', array(
        'consumer_key' => OAUTH_CONSUMER_KEY,
        'consumer_secret' => OAUTH_CONSUMER_SECRET
      ));
      
      if (is_object($req = $this->twitter->authenticate())) {
        // Do something with the $req you received ...
      }
    }
      
The library requires both the TwitterOAuth and OAuth libraries, both available to download from Abraham's [GitHub][5] account. Installation is the same as with any other library, but you need to enable the `$_GET` array to receive data from Twitter when authenticating. You can download it from my [Github][6] account.

[1]: http://www.informationarchitects.jp/en/
[2]: http://www.twitter.com
[3]: http://github.com/abraham/twitteroauth
[4]: http://www.codeigniter.com/
[5]: http://github.com/abraham/
[6]: https://github.com/beseku/CodeIgniter.Twitter