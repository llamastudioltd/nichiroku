---

title: Developing on OS X, pt. 1
slug: developing-on-os-x-part-one
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2006-03-19T00:00:00+00:00

draft: true

---

_This article relates to installing and working with Apache, <abbr>PHP</abbr> and MySQL in OS X 10.4. These instructions may be out of date on later versions of OS X._

Mac <abbr title="Macintosh Operating System Ten">OS X</abbr> comes pre-installed with possibly the most popular, secure and easy to use web server available to the modern web developer, but it does take some tweaking to get it working as a suitable testbed and prototyping environment before you move our applications over to your live servers.

## Where To Store Your Documents

The first step in setting up your server is working out what you need to host, where to put the files in Finder and how to see it in your web browser. Apache serves its documents from `/Library/Webserver/Documents/` and this is the best place to store your files. If, like me, you use various hosting companies, you'll probably want to organise your files further—I tend to reflect my set up on the live server in my development server so it looks nice and organised in Transmit.

## Setting Up Nicer Local <abbr title="Universal Resource Location">URL</abbr>s

Once you have created your folder structure and moved your files, go to `http://127.0.0.1` in your browser and you should see your folder structure reflected through Apache. This is nice, but in order to view your local projects you will probably end up with long, ugly and possibly broken <abbr title="Universal Resource Locations">URL</abbr>s. This can be fixed by setting up 'host names'—local <abbr>URL</abbr>s you add only to your machine so you can use addressing conventions more in line with those in your live environment. To add or modify these host names, you'll need to do the dirty and open the Apache configuration file—the httpd.conf file. I recommend using [Textmate], (for all text-editing, not just this), in which case you need to select 'View hidden files’ in the open dialogue to get at the configuration file. It is located in `/etc/httpd/`.

In the file, (around line 1060) there is an option preceded by a hash, 'Name VirtualHost *:80'. Remove the hash to enable this option, (hashes are comments you know). You then need to add a virtual name host for each of the <abbr>URL</abbr>s you wish to set up, as well as a default entry for localhost, the root of your Apache server, (located at 127.0.0.1).

    # Default for 127.0.0.1 - it makes sure that localhost works.
    <VirtualHost *:80>
      DocumentRoot /Library/WebServer/Documents/
      ServerName localhost
    </VirtualHost>
    # Add new hosts here for development
    <VirtualHost *:80>
      DocumentRoot /Library/WebServer/Documents/dreamhost/beseku.com/v9/
      ServerName www.beseku.dev
    </VirtualHost>


The code above creates two virtual name hosts—the first is the default entry pointing at `http://localhost` and the second is for `http://www.beseku.dev`, a development version of this very site. The first parameter is the physical location of the directory and the second is the <abbr>URL</abbr> you wish to use. Take care when adding addresses that you don't use a <abbr>URL</abbr> currently in use on the web—your machine will always go to your files instead and you won't be able to view the site!

## Setting Up Nicer Local <abbr title="Universal Resource Location">URL</abbr>s: Netinfo Manager

That isn't quite it for the local addresses, you have told Apache where to find the files for that <abbr>URL</abbr> but you also need to tell <abbr>OS X</abbr> that the address is a local one. Open Netinfo Manager, (`Applications/Utilitites`) and select the 'machines' option in the second column. This will list a number of hosts your Mac uses to reference the web server. Duplicate 'Localhost’ and replace the name value in your duplicate with that of the host you created in Apache. Save this when prompted and restart personal web sharing. You should now have a test <abbr>URL</abbr> set up pointing to your development files.

## Using .htaccess

Its very Web 2.0, (don't), to have nice tidy addresses without ugly query strings in the <abbr>URL</abbr>. To accomplish this, you will need to make use of the .htaccess file—a kind of local configuration file for the current folder. I won't tutor on the .htaccess file because I am no expert. The reason I mention them is because in Mac <abbr>OS</abbr> they are disabled by default. To enable them, you will need to once again open the httpd.conf file and alter another option.

    # This controls which options the .htaccess files in directories can
    # override. Can also be "All", or any combination of "Options", "FileInfo",
    # "AuthConfig", and "Limit"
    AllowOverride None


You need to change this to the following to enable .htaccess files on your web-server.

    # This controls which options the .htaccess files in directories can
    # override. Can also be "All", or any combination of "Options", "FileInfo",
    # "AuthConfig", and "Limit"
    AllowOverride All

Save the file and you should now have access to all the [.htaccess voodoo][1] you want. Roberts your father's brother, you've set up Apache to work like it should!

The [second part][2] of this tutorial will focus on getting the latest versions of <abbr title="PHP: Hypertext Pre-processor">PHP</abbr> and MySql installed on your machine and introduce some nifty tools you can use to make it all a bit easier to play with, (and help you to avoid the terminal).

[1]: http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html
[2]: /blog/2006/03/27/developing-on-os-x-part-two/
[3]: http://macromates.com/