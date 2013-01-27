# Command Line GitHub client (CLHub)

This is a very rough command line tool to automate some of the tasks related to
gists and web hooks.

More in detail:

* is written in Python,
* is based on [GitHub API v3](http://developer.github.com/v3/),
* uses [OAuth2](http://developer.github.com/v3/#authentication) authentication,
* the only (external) dependency is [curl](http://curl.haxx.se/), used to handle HTTP.

A list of available subcommands:

	$ ./clhub -h
	usage: clhub [-h] [--version] {gmk,gup,auth} ...

	subcommands:
	    auth                obtain an authorization token
	    gmk                 post the contents of a file in a new gist
	    gup                 update the contents of a file in a gist

	optional arguments:
	  -h, --help            show this help message and exit
	  --version             show program's version number and exit

To perform authenticated tasks, you must first use the `auth` subcommand that
will *register* an "Authorized application" named "Clhub (API)" under the suer
profile using simple HTTP authentication (i.e., requiring the user password on
the command line) and then it will sore the obtained OAuth2 token in
`–/.clhub-tokens.json`. To *revoke* such authorization you'll need to edit the
`USER` GitHub profile (under the "Applications" section).


## Why an external dependency

When first released, this tool could have used the wonderful [Requests: HTTP for
Humans](http://python-requests.org), but [apparently](https://github.com/kennethreitz/requests/issues/179#issuecomment-3324176)
at that time there aws an issue with the order of parameters with for [Browser Uploads to S3 using HTML POST Forms](http://aws.amazon.com/articles/1434).

Now I've no time to rewrite it, but any help will be more than welcome!

## What needs to be done

At least three issues should have been addressed (but I haven't had the time yet):

* add reasonable error handling and reporting,
* add method documentation,
* add a minimalistic manual page.

I promise to do this as soon as I'll find some spare time, but I still find
the tool ussable and it saved me some time – so I'm sharing it even if it is
very rough.

## Where are the downloads related commands gone?

Due to [Goodbye, Uploads](https://github.com/blog/1302-goodbye-uploads) the
support for downloads has been removed; you can check the
[downloads_support](https://github.com/mapio/clhub/tree/downloads_support) tag
if you are interested in the latest version supporting them.

