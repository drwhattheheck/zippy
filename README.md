zippy
=====

A bash script for extracting zipfile submissions to the Google Assignments LMS app,
although it could trivially be modified to work with Google Classroom instead
since they both interact with Google Drive in the same way.

Prerequisite
------------

You will want to make sure that Google Drive is mounted in some way.  On
Windows or MacOS, you can just use Google Drive File Stream or Google Drive
Backup and Sync.  Google doesn't provide solutions like this for Linux, so
you'll have to use something like
[google-drive-ocamlfuse](https://github.com/astrada/google-drive-ocamlfuse)
for that.

Installation
------------

This project uses a submodule, so if you want to clone it, you'll have to add
the `--recursive` option to your command.  Otherwise, the scripts in the
submodule will not be cloned and you won't be able to invoke `zippy`.

    git clone --recursive git://github.com/drwhattheheck/zippy.git

Usage
-----

Currently, `zippy` is just a wrapper around the `ziptools` submodule that makes
assumptions about the path to Google Drive and looks for files in multiple
subdirectories.

    usage: zippy <subcommand> <LabID>
    subcommands:
        canvass <LabID>
        collect <LabID>

    For help with a a subcommand, run:
    zippy <subcommand> -h|--help

Future
------

A couple of things could be done to make the script a bit more useful:

1. Adding another subcommand reformats the submission in the following ways:
   - running `chmod u+r` on all of the extracted sources
   - removing any extracted binaries (sometimes these are old and the sources
     doesn't actually compile)
2. Adding another subcommand that sends the submissions to
   [MOSS](https://theory.stanford.edu/~aiken/moss/).

Both of these could also be added as options to the `collect` subcommand.
