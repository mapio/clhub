# Command Line GitHub client (CLHub)

This is a very rough command line tool to automate some of the tasks related to 
repository downloads and gists.

More in detail:

* is written in Python,
* is based on [GitHub API v3](http://developer.github.com/v3/),
* uses [OAuth2](http://developer.github.com/v3/#authentication) authentication,
* the only (external) dependency is [curl](http://curl.haxx.se/), used to handle HTTP.

You can invoke it as

	./clhub -h

to get a list of availabel subcommands (and relative options)

To perform authenticated tasks, you must first use the `auth` subcommand that 
will *register* an "Authorized application" named "Clhub (API)" under the suer 
profile using simple HTTP authentication (i.e., requiring the user password on 
the command line) and then it will sore the obtained OAuth2 token in 
`–/.clhub-tokens.json`. To *revoke* such authorization you'll need to edit the 
`USER` GitHub profile (under the "Applications" section).


## Why an external dependency

This tool could have used the wonderful [Requests: HTTP for
Humans](http://python-requests.org)), but [apparently](https://github.com/kennethreitz/requests/issues/179#issuecomment-3324176)
there is an issue with the order of parameters with for [Browser Uploads to S3 using HTML POST Forms](http://aws.amazon.com/articles/1434).

## What needs to be done

At least two issues should really be addressed soon:

* add reasonable error handling and reporting,
* add method documentation,
* add a minimalistic manual page.

I promise to do this as soon as I'll find some spare time, but I still find
the tool ussable and it saved me some time – so I'm sharing it even if it is
very rough.
