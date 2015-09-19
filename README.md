blogit – the almost too uncomplicated bash blogger
===============================================

**NOTE: blogit is handcrafted for my needs, powering my website, and most likely won't serve you, unless you configure it for your own needs. It doesn't treat the server as a black box – blogit actually needs to know a few things about your servers inner workings. That said, feel free to check it out. Below are instructions if you still want to use it for your own needs.**

Blogit powers [hjorthjort.com](http://www.hjorthjort.com)

Blogit pushes markdown to a specified server and "publishes" them.

What you need:
-------------

* A shell that runs bash scripts.
* A server for hosting.
* Login credentials for that server or access via ssh key.
* A blogpost written in markdown or html.

What it does:
-------------

What you have to do is this: 

1. Open blogit in your texteditor and set your username and IP to the preferred values in the top of the document. Also change the variable rootpath to reflect the place on your server where you want your posts to go. You only have to do this once.
1. Create a folder called blog-posts on your server where you want your posts to go, under the folder you set as rootpath.
1. cd into folder with your post (optional, but gives you more managable, legible and less revealing filenames in the end).
1. On the command line, write "blogit publish <name of your post file>". For example: "blogit publish README.md".

Blogit then does the following:
-----------------------------

1. Converts your post to html using pandoc.
1. Enters your server via ssh. If you don't have an ssh key, you will have to enter your password here.
1. Writes the post to a new file with the same name as your post, with an added ".html" at the end. For example "README.md.hmtl".
1. Creates a file called .post-index.txt and writes the path name of your new post at the top of that file. For example "~/my-site/blog-posts/README.md.html".

You can now have html posts as well as an index sorted in reverse chronological order over the posts in your blog-posts file. 

The way I use this is that I in index.php at my site do a foreach loop over the lines in .post-index.txt and for each of them I print out the contents of the file that line points to, as well as any additional information I want to add, like timestamps, horisontal divisors and such. I also use the contents of .post-index.txt to create a list over recent blogposts at the top of my site, complete with links to these posts.
