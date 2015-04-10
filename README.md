go-embedded
===========

Go package for embedded Linux development.

## Cross-compiling notes

The following script can be used to cross-compile the various modules for
an ARM Linux system:

    #!/bin/bash
    cmd="$1"
    shift

    export CC=arm-linux-gnueabi-gcc
    export GOARCH=arm
    export GOOS=linux
    GOARM=5 CGO_ENABLED=1 go $cmd -ldflags="-extld=$CC" "$@"

The `GOARM=5` setting is required for software floating-point support.
