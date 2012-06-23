# Python GitHub-downloads Uploader

This is a very rough command line tool to automate the upload of files to the
GitHub repositories downloads section.

More in detail:

* is written in Python,
* is based on [GitHub API v3](http://developer.github.com/v3/),
* uses [OAuth2](http://developer.github.com/v3/#authentication) authentication,
* the only (external) dependency is [curl](http://curl.haxx.se/), used to handle HTTP.

You can invoke it as

	./github-downloads-upload USER REPO FILE DESCRIPTION

to upload file `FILE` to repository `REPO` of user `USER` with description `DESCRIPTION`.

The *first time* you use it it will register an "Authorized application" named
"Downloads Uploader (API)" under `USER` profile using simple HTTP
authentication (i.e., requiring the `USER` password) and then it will sore the
obtained OAuth2 token in `–/.gdu-tokens.json`. To *revoke* such authorization
you'll need to edit the `USER` GitHub profile (under the "Applications" section).

## What else is there

There are two other scripts to list and delete downlods. Invoke the first as

	./github-downloads-list USER REPO

and

	./github-downloads-delete USER REPO DLID

where `DLID` is the download ID reported in the first column of the previous
command output.

## Why an external dependency

This tool could have used the wonderful [Requests: HTTP for
Humans](http://python-requests.org)), but [apparently](https://github.com/kennethreitz/requests/issues/179#issuecomment-3324176)
there is an issue with the order of parameters with for [Browser Uploads to S3 using HTML POST Forms](http://aws.amazon.com/articles/1434).

## What needs to be done

At least two issues should really be addressed soon:

* add reasonable error handling and reporting,
* consider the possibility to develop a real Python package to avoid code duplication.

I promise to do this as soon as I'll find some spare time, but I still find
the tool ussable and it saved me some time – so I'm sharing it even if it is
very rough.
