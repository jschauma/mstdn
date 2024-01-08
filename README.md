mstdn - a bare bones Mastodon command-line client
=================================================

(I just can't bring myself to say "toot".)

`mstdn` is a yanky shell script to let me post to
Mastodon from the command-line.  It's similar in
spirit to my [twitter cli
tool](https://github.com/jschauma/tweet), but being
in its infancy right now, it only allows posting an
update (with media).

Requirements
------------
`mstdn` is written in shell, but it requires `curl`.


Installation
------------
To install the command and manual page somewhere
convenient, run make install; the Makefile defaults to
'/usr/local' but you can change the PREFIX:

```
$ make PREFIX=~ install
```

Documentation
-------------
Please see the manual page for all details:

```
NAME
     mstdn -- send a mastodon update

SYNOPSIS
     mstdn [-hiv] [-d descr] [-m media] [-s server] [-t file]

DESCRIPTION
     mstdn is a very simple tool to send a Mastodon update to the given server
     - nothing else.  The message to send is read from STDIN; the account to
     post as is defined via the access token found in the file passed to -t.

OPTIONS
     The following options are supported by mstdn:

     -d descr	Use the given description for the media to be uploaded via -m.
		Use quotes for strings including spaces.

     -h		Print a short usage statement and exit.

     -i		Print the resulting message ID.

     -m media	Upload and attach the given media (picture or video).

     -s server	Post the update to this Mastodon server.  Default:
		mstdn.social

     -t file	Read the access token from this file.  Default:
		~/.mstdn/<server>

     -v		Be verbose.  Can be specified multiple times to increase ver-
		bosity.

AUTHORIZATION
     In order to use mstdn, you will need to get an access token and place it
     into a file.  The token can be retrieved by going to Preferences->Devel-
     opment on your Mastodon server and adding a "new application".  The
     application will only need the "write:media" and "write:statuses" privi-
     leges.  After creating the application, you should be able to copy the
     "access token" from the application details.

EXAMPLES
     The following examples illustrate common usage of this tool.

     To send a simple message to the default Mastodon server reading the
     access token from the default location:

	   echo "I can't believe I used the word 'toot'." | mstdn

     To post the contents of the file 'msg' together with the image 'file.jp'
     to the 'chaos.social' instance using an access token from the file
     '~/mytoken':

	   mstdn -t ~/mytoken -s chaos.social -m file.jpg <msg

EXIT STATUS
     The mstdn utility exits 0 on success, and >0 if an error occurs.

ENVIRONMENT
     The following environment variables affect the execution of this tool:

     MASTODON_SERVER  The Mastodon server to post the update to.  The -s flag
		      overrides this value.

     TOKEN_FILE	      The file to read the access token from.  The -t flag
		      overrides this value.  If not specified, then this value
		      defaults to the pathname ~/.mstdn/${MASTODON_SERVER}.

HISTORY
     mstdn was originally written by Jan Schaumann <jschauma@netmeister.org>
     in December 2022.

BUGS
     Please file bugs and feature requests via GitHub pull requests and issues
     or by emailing the author.
```
