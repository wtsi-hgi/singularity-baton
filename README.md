# baton, contained

A Singularity container and wrapper script for
[baton](wtsi-npg.github.io/baton).

## Usage

The Singularity image can be built from the [recipe file](baton.def) and
placed somewhere in your `PATH` or alongside the wrapper script. (Note
that the wrapper script will build the image automatically if it cannot
find it in the aforementioned locations.)

The wrapper script runs the baton image with the given arguments. It
will automatically bind mount your iRODS environment configuration,
associated dependencies and, if necessary, Kerberos configuration. If
you specify any `--file` arguments, those will also be mounted in the
container transparently.

Note that the baton suite of programs are prefixed with `baton-` (e.g.,
`baton-list`). The image exposes these instead as separate apps and they
can be used through the wrapper script as subcommands. For example:

    baton -c "/my/collection" | baton-metaquery --obj

...should be rewritten as:

    baton -c "/my/collection" | baton metaquery --obj
