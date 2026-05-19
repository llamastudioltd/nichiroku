---

title: A MarsEdit friendly XML-RPC server in CodeIgniter
slug: a-marsedit-friendly-xml-rpc-server-in-codeigniter
summary: Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.

date: 2010-01-26T00:00:00+00:00

draft: true

---

Part of the custom software powering the new version of this site is a small and very basic MetaWeblog <abbr title="Application Programming Interface">API</abbr> compatible <abbr title="">XML</abbr>-<abbr title="">RPC</abbr> server, allowing me to manage the weblog section of the site via software such as [MarsEdit][1], a tool I previously used when editing my Expression Engine powered website. The decision to build such a solution came from not wanting to build any kind of web-based back-end, but also not wanting to have to edit database rows directly to make posts. As [CodeIgniter][2] contains an <abbr>XML</abbr>-<abbr>RPC</abbr> library, (for which there isn't much in the way of good documentation, or many examples on how to interact with common <abbr>API</abbr>s such as this one), I thought it would be simple. It wasn't, so I uploaded some examples to help others navigate through the problems I encountered.

I've uploaded a controller similar to the one used on this site, and added additional comments to guide users. The controller, which initialises the server, only makes use of the MarsEdit interpretation of the MetaWeblog <abbr>API</abbr>, consisting of seven of the methods documented here on [Microsoft.com][3]. There are no methods implemented for returning information on the user or the blogs available. If these methods are required in future releases, they should be pretty simple to implement based on the examples laid out here.

I've also enclosed an example model file that demonstrates user authentication and shows how requests could be used to manipulate a weblog's contents. There is no real information manipulation since there is no database layer, but the model shows enough about the format that the data should be in and the parameters that each request passes through.

Finally, I created a simple <abbr>XML</abbr>-<abbr>RPC</abbr> helper file that takes the array structures returned by the default CodeIgniter database class and converts them to the `struct` format that is required when sending responses via the MetaWeblog <abbr>API</abbr>. I found the `struct` format confusing to read and messy to implement in <abbr title="PHP:Hypertext Pre-processor">PHP</abbr> so using a helper allowed me to abstract this away somewhat, keeping the core code much tidier. On this website I also use [Markdown][4] as a means of formatting my posts. It's relatively simple to integrate Markdown into CodeIgniter as a helper - just download the [latest <abbr>PHP</abbr> implementation][5] and save it as `markdown_helper.php` in your application's helpers directory.

The files are available to download from [GitHub][6]. The default CodeIgniter file structure has been preserved but only the files I created are present. Please fork the repository if you find any bugs or make any improvements.

[1]: http://www.red-sweater.com/marsedit/
[2]: http://www.codeigniter.com/
[3]: http://msdn.microsoft.com/en-us/library/bb259697.aspx
[4]: http://daringfireball.net/projects/markdown/
[5]: http://michelf.com/projects/php-markdown/
[6]: https://gitlab.com/beseku/CodeIgniter.MetaWeblogDemo