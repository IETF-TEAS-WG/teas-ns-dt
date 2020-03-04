# Framework for Transport Network Slices

This is the working area for an Internet-Draft in preparation by the TEAS WG's network slicing design team.

## Building the Draft

Formatted text and HTML versions of the draft can be built using `make`.

```sh
$ make
```

Before you can do this, you will need to download the latest MD format file, and Makefile.  You may also have to strip out any HTML wrapper text (header/footer) in both of these files.

This requires that you have the necessary software installed. Namely, you will need "make", "kramdown-rfc2629" and "xml2rfc". See
[the instructions](https://github.com/martinthomson/i-d-template/blob/master/doc/SETUP.md) for setting these tools up.

Note also that - depending on your OS and development environment - you may have to get (download) other tools to make the above tools work.  Mostly, remember "google is your friend."


## Contributing

See the
[guidelines for contributions](https://github.com/teas-wg/teas-ns-dt/framework/blob/master/CONTRIBUTING.md).

## Building the ".txt" version in this repository

The best way I (Eric Gray) have discovered for doing this is to use a unix-like command line to pull the repository.

For example, using a Mac enviroment, after working through the steps described above, use the following steps:

1) go to a directory where you want to start working
2) "git clone https://github.com/teas-wg/teas-ns-dt.git"
   (this makes a local copy of the entire repository)
3) "cd teas-ns-dt/framework"
4) "make"

This can be done for your branch if you have created a pull.  It is helpful if you make sure that any changes you make "compile" to make the ".txt" file you expect before the pull is merged back into the master branch.

If you have completed any changes you wish to make in the local files, use the following steps to upload the changed file (using README.md as an example):

- "git add README.md"

For the local repository owner (the Editors for this draft), complete the following steps to finish:

- "git commit -m'some usefull message, perhaps a summary of the changes'"
- "git push"


