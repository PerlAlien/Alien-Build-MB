# Alien::Build::MB ![static](https://github.com/PerlAlien/Alien-Build-MB/workflows/static/badge.svg) ![linux](https://github.com/PerlAlien/Alien-Build-MB/workflows/linux/badge.svg) ![windows](https://github.com/PerlAlien/Alien-Build-MB/workflows/windows/badge.svg) ![macos](https://github.com/PerlAlien/Alien-Build-MB/workflows/macos/badge.svg)

Alien::Build installer class for Module::Build

# SYNOPSIS

In your Build.PL:

```perl
use Alien::Build::MB;

Alien::Build::MB->new(
  module_name => 'Alien::MyLibrary',
  ...
);
```

# DESCRIPTION

This is a [Module::Build](https://metacpan.org/pod/Module::Build) subclass that uses [Alien::Build](https://metacpan.org/pod/Alien::Build) to
help create [Alien](https://metacpan.org/pod/Alien) distributions.  The author recommends
[Alien::Build::MM](https://metacpan.org/pod/Alien::Build::MM), which uses [ExtUtils::MakeMaker](https://metacpan.org/pod/ExtUtils::MakeMaker) instead.
The primary rationale for this class, is to prove independence
from any particular installer, so that other installers may be
added in the future if they become available.  If you really do
prefer to work with [Module::Build](https://metacpan.org/pod/Module::Build) though, this may be the
installer for you!

# CONSTRUCTOR

## new

```perl
my $abmb = Alien::Build::MB->new(%args);
```

Takes the usual [Module::Build](https://metacpan.org/pod/Module::Build) arguments.

# PROPERTIES

All [Alien::Build::MB](https://metacpan.org/pod/Alien::Build::MB) specific properties have a `alien_` prefix.

## alien\_alienfile\_meta

If true (the default), then extra meta will be stored in `x_alienfile` which includes
the `share` and `system` prereqs.

# METHODS

## alien\_build

```perl
my $build = $abmb->alien_build;
```

Returns a freshly deserialized instance of [Alien::Build](https://metacpan.org/pod/Alien::Build).  If you make
any changes to this object's `install_prop` or `runtime_prop` properties
be sure that you also call `$build->checkpoint`!

# ACTIONS

These actions should automatically be called during the normal install
process.  For debugging you may want to call them separately.

## ACTION\_alien\_download

```
./Build alien_download
```

Downloads the package from the internet.  For a system install this does
not do anything.

## ACTION\_alien\_build

```
./Build alien_build
```

Build the package from source.

## ACTION\_alien\_test

```
./Build alien_test
```

Run the package tests, if there are any.

# SEE ALSO

[Alien::Build](https://metacpan.org/pod/Alien::Build), [Alien::Build::MM](https://metacpan.org/pod/Alien::Build::MM), [Alien::Base::ModuleBuild](https://metacpan.org/pod/Alien::Base::ModuleBuild)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017-2022 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
