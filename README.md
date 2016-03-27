# SeaHUG "Parallel and concurrent programming in Haskell" materials

## About the book

To get more information about the source text "Parallel and Concurrent
Programming in Haskell" by Simon Marlow, please visit the [book's web
site][book]. You can purchase the book or read it online there for free.

## Building the code samples

None of the steps described in this document are necessary in order to take a
full part in the course, since we assume minimal prior experience with Haskell.

However, if you do wish to build the code samples, this document describes
perhaps the two most common methods: using a [Cabal sandbox](#cabal-sandbox)
and using a [Docker container](#docker-container). The instructions given here
are specific to Linux, though you should be able to get equivalent results on
Windows and Mac OS X&mdash;do note, however, that building/installing Haskell's
network-related packages is [notoriously difficult][network-windows], though
not impossible, on Windows.

Note that you can also follow the [official instructions][official] from the
online version of the book.

### <a name="cabal-sandbox"></a>Install and build using a Cabal sandbox

This approach assumes that you have a working installation of [GHC][ghc]
including the [`cabal-install`][cabal-install] package. These steps have been
tested with GHC 7.10.2, though GHC 7.10.3 and GHC 7.8.4 should also work.

```bash
$ git clone https://github.com/seahug/parconc-examples.git
$ cd parconc-examples/
$ cabal sandbox init
$ cabal install --only-dependencies
$ cabal build
```

### <a name="docker-container"></a>Install and build in a Docker container

This method relies on [Docker][docker] and the standard [Haskell
image][haskell-docker] from Docker Hub. This approach will ensure you are using
the latest compatible GHC compiler in a completely isolated environment. The
instructions also assume that you have a working version of [GNU
Make][gnu-make] on your system, which is almost always the case.

#### Install Docker

[Follow the Docker installation instructions][docker-install].

#### Build Docker image

The `Makefile` file in the `examples` directory can be used to create a Docker
image based on the standard Haskell base image. Note that we clone the Git repo
using the `--recursive` switch in order to clone all the repo's submodules.

```bash
$ git clone --recursive https://github.com/seahug/pcph.git
$ cd pcph/examples/
$ make
```

#### Run Docker container

The `Makefile` can also be used to run a Docker container from the image
created in the previous step. From the `pcph/examples` directory:

```bash
$ make run
```

This will start the Docker container and connect your terminal to its shell.

### Build code samples inside Docker container

Inside the Docker container's shell, you can initialize the sandbox and build
the code as follows:

```bash
$ cd /src/
$ cabal sandbox init
$ cabal install --only-dependencies
$ cabal build
```

The resulting binaries will be placed in the `dist/build` directory.

# Licence

Released under MIT License

[book]: http://chimera.labs.oreilly.com/books/1230000000929
[cabal-install]: https://wiki.haskell.org/Cabal-Install
[docker-install]: https://docs.docker.com/engine/installation/
[docker]: https://www.docker.com/
[ghc]: https://www.haskell.org/downloads
[gnu-make]: https://www.gnu.org/software/make/
[haskell-docker]: https://hub.docker.com/_/haskell/
[network-windows]: http://neilmitchell.blogspot.com/2010/12/installing-haskell-network-library-on.html
[official]: http://chimera.labs.oreilly.com/books/1230000000929/ch01.html#sec_sample
