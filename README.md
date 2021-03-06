kiln-local-backup
=================

Make local backups of repositories stored on Fog Creek Software's Kiln.

A fork of http://code.google.com/p/kiln-local-backup/.

ORIGINAL README
===============

LICENSE

  Copyright (c) 2010 Nate Silva

  Permission is hereby granted, free of charge, to any person obtaining a copy
  of this software and associated documentation files (the "Software"), to deal
  in the Software without restriction, including without limitation the rights
  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the Software is
  furnished to do so, subject to the following conditions:

  The above copyright notice and this permission notice shall be included in
  all copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
  SOFTWARE.

OVERVIEW

  This is a backup script to maintain a copy of all of your Kiln Mercurial
  repositories on your local system.

GETTING STARTED

  For Windows you need:

    * A Kiln account
    * A FogBugz API token
    * Python 2.4 or higher
    * simplejson (not needed with Python 2.6 or higher)
    * The Kiln Tools installed

  On other platforms, you’ll also need to install:

    * Mecurial 1.3 or higher
    * The KilnAuth Mercurial extension

  If you are missing any of these, see REFERENCES at the end of this document.

BACKING UP

  All repositories are backed up to the directory you specify. For example, if
  you want to back up to C:\KilnBackups, run:

      python kiln-local-backup.py C:\KilnBackups

  You will be prompted for your API token and Kiln server name. If your
  credentials aren’t stored in KilnAuth, you’ll also be prompted for your
  password.

  Your API token and server name are saved to a file in the backup directory,
  so you won’t have to enter them next time.

  Once KilnAuth has your credentials, you will not be prompted for your
  password again.

  To see the full syntax, including options for passing your API token and
  server name on the command line, type:

      python kiln-local-backup.py --help

FAQS

  Q: My backup is empty!

  A: No, it’s not. With Mercurial, the entire repository is stored in the .hg
     subdirectory, which may be hidden. You can clone the repository to see
     that the files are really there, if it makes you feel better.

     Alternately, you can specify the --update command-line option. Then you’ll
     see your working files. The working files that you see are just the latest
     version of your project, but rest assured the script is backing up your
     whole repository, including all history. That’s located in the .hg
     subdirectory.


  Q: Scheduled backups don’t work.

  A: Make sure you are running the backup under THE SAME USER ACCOUNT you were
     using when you entered your password for KilnAuth.


  Q: What platforms does this run on?

  A: I have tested it on Mac OS X 10.6, Windows Server 2003 R2, and Ubuntu
     Linux 9.10.


  Q: Can I back up repositories with non-ASCII names?

  A: It should work. On Windows, non-ASCII characters in the repository name
     will be replaced with equivalent XML character references. On Unix/Mac,
     non-ASCII names will be used as-is.

REFERENCES

  To get a FogBugz API token, see: http://goo.gl/rGDQ9

  To get the KilnAuth Mercurial extension, install the Kiln Client, or see your
  Kiln Tools page. The URL is: http://[your kiln site]/Tools.

  simplejson is only needed for Python versions earlier than 2.6. It can be
  found at http://goo.gl/nv3tu.