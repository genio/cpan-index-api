# NAME

CPAN::Index::API - Read and write CPAN index files

# SYNOPSIS

```perl
my $index = CPAN::Index::API->new_from_repo_uri(
    repo_uri => 'http://cpan.perl.org/',
    files => [qw(PackagesDetails ModList MailRc)],
);

my $packages = $index->file('PackagesDetails');
```

# DESCRIPTION

`CPAN::Index::API` is a library to read and write CPAN index files. See the
modules in the `CPAN::Index::API::File` namespace for documentation on the
individual files supported.

This class provides a convenient interface for working with multiple files
from the same location at the same time.

# CONSTRUCTION

## new

Creates a new index object. Accepts the following parameters:

- files

    Required. Hashrefs whose values are `CPAN::Index::API::File` objects. The
    individual objects can later be accessed by their respective hash key via the
    ["file"](#file) method.

- repo\_path

    Optional. Path to the root of the repository to which the index files belong.

- repo\_uri

    Optional. Base uri of the repository to which the index files belong.

## new\_from\_repo\_path

Creates a new index object by reading one or more index files from a local
repository. Accepts the following parameters:

- files

    Required. Arrayref of names of index files to be read. Each name must be the
    name of a plugin under the `CPAN::Index::API::File::` namespace, e.g.
    `PackagesDetails`, `ModList`, etc.

- repo\_path

    Required. Path to the root of the local repository.

## new\_from\_repo\_uri

Creates a new index object by reading one or more index files from a remote
repository. Accepts the following parameters:

- files

    Required. Arrayref of names of index files to be read. Each name must be the
    name of a plugin under the `CPAN::Index::API::File::` namespace, e.g.
    `PackagesDetails`, `ModList`, etc.

- repo\_uri

    Required. Path to the base uri of the remote repository.

# METHODS

## file

Given the name of a file plugin loaded within the index, returns the object
corresponding to this index file.

## repo\_path

Returns the path to the repository.

## repo\_uri

Returns the base uri of the repository.

## write\_all\_files

Writes all index files to their default locations under `repo_path`.

## clone

Creates a new instance of this object, overloading any of the existing
attributes with any arguments passed.

# AUTHOR

Peter Shangov <`pshangov@yahoo.com`>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2019 by Venda, Inc.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
