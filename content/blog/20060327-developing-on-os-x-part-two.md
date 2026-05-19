---

title: Developing on OS X, pt. 2
slug: developing-on-os-x-part-two
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2006-03-27T00:00:00+00:00

draft: true

---

_This article relates to installing and working with Apache, <abbr>PHP</abbr> and MySQL in OS X 10.4. These instructions may be out of date on later versions of OS X._

The [first part][1] of this tutorial focused on getting Apache up and running in a way that would hopefully reflect a live server environment. This second part will explain how to get <abbr title="PHP: Hypertext Pre-processor">PHP</abbr> and MySQL, the most popular server side language and database combination, installed on your local machine.

## Installing <abbr>PHP</abbr>

Many old-schoolers would download the latest source from [php.net][2], compile it for their machines with custom modules and install it straight to Apache in <abbr title="Macintosh Operating System Ten">OS X</abbr>. As you may have guessed, this is not my way, instead I prefer to get pre-compiled packages from [Marc Liyanage][3] that can be installed into Apache like you would any other <abbr>OS X</abbr> package. He has all of the latest flavours available—I use <abbr>PHP</abbr> 5 locally to reflect my online environment. Using Marc's excellent packages, you don't need to delve into the httpd.conf file to register file extensions or any other dirty work.

**Update:** I've just upgraded my work system using the latest version of Marc's <abbr>PHP</abbr> packages and short tags—the preferred method of echoing data in frameworks like [CodeIgniter][4]—are not enabled by default. To enable them you need set `short_open_tag = On` in the php.ini file, located in `usr/local/php5/lib/`. The value you need to change should be around line 141 and should be changed to the above. This allows you to use `<?= ?>` tags in your code.

## Installing MySQL

Since version 4.0.11, Marc's packages have been superseded by [similar packages][5] direct from [MySQL][6]—these are exactly the same in that they allow you to install the MySQL database from a one-click package file, and they also helpfully add a system preferences button to give you a bit more control and allow you to run the database at start-up and restart the MySQL server.

## Administering MySQL Users & Databases

As well as the self-installing package, MySQL have released a number of useful tools that make running MySQL a much simpler, and less command-line driven, task.

The first of these tools is [MySQL Administrator][7]—an application that allows you to add and remove users and database schemas. This is the easiest way to maintain your user accounts on the local database and carry out simple database design tasks. I always change my root password from here as it takes far less time than going through the terminal.

The second tool I use extensively is [MySQL Query Browser][8], also from MySQL. This application revolves around database design and allows you to create databases, (called Schemas), stored procedures, (if you use MySQL 5) and add/edit/delete data from your databases. This was the main method of designing and altering the [CheckWithMother][9] databases during development. I should warn you that MySQL Query Browser does suffer from sporadic quitting problems—this is being worked on by the developers but can be quite annoying.

Another advantage of both of these tools is that they allow you to access external databases if your hosting company allows it—this is very useful as I can modify data on a live database if such a need arises.

There are other tools of note that can be used to play with MySQL—in the past I have used both [CocoaSql][10] and [YourSql][11], but neither support stored procedures in MySQL 5 so became less useful when [Dreamhost][12] upgraded their versions.

That's it! You should now be able to run local domains, administer your databases and run <abbr>PHP</abbr>-driven sites all form your local machine. Now lets hope someone makes it just as easy to install and deploy [Ruby on Rails] locally.

[1]: /blog/2006/03/19/developing-on-os-x-part-one/
[2]: http://www.php.net
[3]: http://www.entropy.ch/software/macosx/
[4]: http://www.codeigniter.com
[5]: http://dev.MySQL.com/downloads/MySQL/5.0.html
[6]: http://www.MySQL.com
[7]: http://dev.MySQL.com/downloads/administrator/1.1.html
[8]: http://dev.MySQL.com/downloads/query-browser/1.1.html
[9]: http://www.checkwithmother.com
[10]: http://www.versiontracker.com/dyn/moreinfo/macosx/10887&vid=100949
[11]: http://yoursql.ludit.it
[12]: http://www.dreamhost.com/rewards.cgi?beseku
[13]: http://www.rubyonrails.org/