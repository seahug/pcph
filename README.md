# SeaHUG "Parallel and concurrent programming in Haskell" materials

Materials for "Parallel and concurrent programming in Haskell" course

## Make sure you can build examples from the book

The method described here relies on [Docker][1] and the standard [Haskell
image][2] from Docker Hub. You should be able to achieve comparable results
using the [Haskell platform][3] for your operating system.

### Install Docker

Follow [Docker installation instructions][4].

### Build Docker image and run container

The provided `Makefile` creates a Docker image based on the standard Haskell
base image and can run a container that mounts the `src` directory containing
Simon Marlow's [code samples][5].

```bash
$ git clone https://github.com/seahug/pcph.git
$ cd examples/
$ make
$ make run
```

### Build code samples inside Docker container

```bash
$ cd /src/
$ cabal sandbox init
$ cabal install --only-dependencies
$ cabal build
```

The resulting binaries will be placed in the `dist/build` directory.

# Licence

Released under MIT License

[1]: https://www.docker.com/
[2]: https://hub.docker.com/_/haskell/
[3]: https://www.haskell.org/platform/
[4]: https://docs.docker.com/engine/installation/
[5]: https://github.com/seahug/parconc-examples

