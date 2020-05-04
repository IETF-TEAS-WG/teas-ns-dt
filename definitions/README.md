# Definitions for Transport Network Slices

This is the GitHub working area for the Definitions Internet-Draft in preparation by the TEAS WG's network slicing design team.

## Building the Draft

The formatted text versions of the draft can be built using `make`.

```sh
$ make
```

Before you can do this, you will need to download the latest XML format file, and Makefile.  You may also have to strip out any HTML wrapper text (header/footer) in both of these files.

Note: this part is easier if you're using the command-line interface to GitHub.  If working that way, use "git pull" to get the most recent merged version of files in this directory, and then run "make."

This requires that you have the necessary software installed. Namely, you will need "make", and "xml2rfc". See
[the instructions](https://github.com/martinthomson/i-d-template/blob/master/doc/SETUP.md) for setting these tools up.

Note also that - depending on your OS and development environment - you may have to get (download) other tools to make the above tools work.
Mostly, remember "google is your friend."


## Contributing

See the
[guidelines for contributions](https://github.com/teas-wg/teas-ns-dt/definitions/blob/master/CONTRIBUTING.md).

## Building the ".txt" version in this repository

The best way I (Eric Gray) have discovered for doing this is to use a unix-like command line to "pull" the repository (as described above).

For example, using a Mac enviroment, after working through the steps described above, use the following steps:

1) go to a directory where you want to start working
2) "git clone https://github.com/teas-wg/teas-ns-dt.git"
   (this makes a local copy of the entire repository)
3) "cd teas-ns-dt/definitions"
4) "make"

Thereafter, update your "clone" of the repository, using "git pull" (while in the repository).

This can be done for your branch if you have created a pull.

It is helpful if you make sure that any changes you make "compile" to make the ".txt" file you expect before attempting to merge the pull back into the master branch.

If you have completed any changes you wish to make in the local files, use the following steps to upload the changed file (using README.md as an example):

- "git add README.md"

Note: substitute, or add other files that you have added, or modified to the "git add" command, or subsequent "git" commands will ignore those files (and warn that it has done so).

For the local repository owner (the Editor, or Editors, for this draft), complete the following steps to finish:

- "git commit -m'some usefull message, perhaps a summary of the changes'"
- "git push"

Note: you may have to do "git pull" first, if someone else (possibly yourself) has modified files in the repository under a different pull.

In the event that the same files have been altered during the pull, this is the point at which merging will occur.

If "git push" fails due to unmerged files (i.e. - "git pull" was not run successfully first), you will need to use "git push" again.
