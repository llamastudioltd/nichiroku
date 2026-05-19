---

title: Enabling mod_rewrite in OS X 10.5 & 10.6
slug: enabling-mod_rewrite-in-mac-os-105-106
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2009-01-04T00:00:00+00:00

draft: true

---

Apache's [mod_rewrite][1] functionality allows you to redirect and rewrite your web site <abbr title="Universal Resource Loaction">URL</abbr>s, providing a developer with an easy way of creating human readable, well structured and, most importantly, navigable page addresses. It's used by almost all Apache-based software from [Wordpress][2] to [Codeigniter][3]. Enabling it within Apple's latest iteration of Mac OS X is, unfortunately, a bit of a fiddle.

Updating the Apache configuration to allow the use of this functionality is achieved by modifying two files, one for the global web-server directory and one for your local web-server directory, (the much easier-to-access `~/Sites` folder). The first file to be modified is the global configuration file, and it needs to be modified around line 205.

    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    # Options FileInfo AuthConfig Limit
    AllowOverride All

The second file, allowing you to use mod_rewrite within your own `~/Sites` folder, is the one that seems to break Apache on a more regular basis. The values below, located at the top of the file, yielded the best results, enabling the functionality without causing server errors.

    <Directory "/Users/beseku/Sites/">  
      Options Indexes FollowSymLinks MultiViews
      AllowOverride All AuthConfig
      Order allow,deny
      Allow from all
    </Directory>

After making and saving these changes, you'll need to restart Apache, (easily done via the ’sharing' system preference pane, just un-check then re-check the 'Web Sharing’ checkbox). If everything went well, Apache should start up again and you should have full mod_rewrite functionality.

[1]: http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html
[2]: http://www.wordpress.com
[3]: http://www.codeigniter.com
