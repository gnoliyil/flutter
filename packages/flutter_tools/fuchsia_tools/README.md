This directory serves as a placeholder directory for the package roots of
various fuchsia tools which use the flutter_tools library.

This is required to provide a workaround for the fuchsia build system.
When this directory is not present the various tools specified in the
`dart_tool` directives in the flutter_tools/BUILD.gn file will end up
having the same package root entry written in the .packages file. This
causes the build to fail because the dart compiler has a requirement that
libraries must have a unique package uri. By specifying a package root which
is a subdirectory of this directory for these tools we avoid having the build
system create duplicate package roots for the generated libraries for these
tools.

Note that we cannot move the location of the main files for these tools because
the paths are hard coded in the fuchsia tree.
