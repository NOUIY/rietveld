# WARNING: The Rietveld server on App Engine may disappear!

By Guido van Rossum (Rietveld's original creator).

I keep receiving emails from Google indicating that I have to do some kind of work to keep it
(and all my other App Engine apps) running. I don't speak their language any more, so I will just give up.
Unless someone is interested in taking over ownership of this Rietveld instance, it will eventually disappear.

Sorry.

Welcome to Rietveld
-------------------

GitHub Wiki: https://github.com/rietveld-codereview/rietveld/wiki
Google Group: http://groups.google.com/group/codereview-discuss

This project shows how to create a somewhat substantial web
application using Django on Google App Engine.  It requires Python 2.7
and Django version 1.3 (although a previous version using Python 2.5
and Django 1.2 can still be found in the py25 branch in the repository).

In addition, I hope it will serve as a practical tool for the Python
developer community, and hopefully for other open source communities.
As I've learned over the last two years at Google, where I developed a
similar tool named Mondrian, proper code review habits can really
improve the quality of a code base, and good tools for code review
will improve developers' life.

Some code in this project was derived from Mondrian, but this is not
the full Mondrian tool.

--Guido van Rossum, Python creator and Google employee

Links
-----

- Mondrian video: http://www.youtube.com/watch?v=sMql3Di4Kgc
- Google App Engine: http://code.google.com/appengine/
- Live app: https://codereview.appspot.com
- About code review: http://en.wikipedia.org/wiki/Code_review
- Django: http://djangoproject.com
- Python: http://python.org

License
-------

The license is Apache 2.0.  See the file COPYING.

Running
-------

To run the app locally (e.g. for testing), download the Google App
Engine SDK from http://code.google.com/appengine/downloads.html.  You
can then run the server using
```
  make serve
```
(assuming you're on Linux or Mac OS X).  On Windows just use Google
App Engine Launcher.

Please make sure that you have the most recent version of the App Engine SDK
installed when running Rietveld locally. That's the version that runs in the
production environment too and Rietveld often uses new features.

The server is only accessible on http://localhost:8080.  The server in
the Google App Engine SDK is not designed for serving real traffic.
The App Engine FAQ at https://developers.google.com/appengine/kb/general
says about this: "You can override this using the -a <hostname> flag
when running it, but doing so is not recommended because the SDK has
not been hardened for security and may contain vulnerabilities."

To deploy your own instance of the app to Google App Engine:

  1. Register your own application ID on the App Engine admin site.
  2. Edit app.yaml to use this app ID instead of 'codereview-hr'.
  3. Upload using
     ```
       make update VERSION=123f
     ```

**Don't forget step 2!  If you forget to change the application ID,
you'll get a error message from "appcfg.py update" (called by "make
update") complaining you don't have the right to administer this app.**

The VERSION=xxx argument sets the version; the version from the
app.yaml is not used.  This is to support a convention used for the
main Rietveld instance (codereview.appspot.com) whereby we never
deploy to the same version twice; the version must be manually picked
by the developer doing the deployment.  If you don't like this, just
edit the Makefile to remove "--version $(VERSION)" and edit app.yaml
to hardcode a version number.

Administration
--------------

Various jobs to administer an instance are collected in admin_tasks.py. These
jobs can be run by an instance administrator by visiting
http://your-instance/mapreduce/.
