# Alien::Build::MB [![Build Status](https://secure.travis-ci.org/plicease/Alien-Build-MB.png)](http://travis-ci.org/plicease/Alien-Build-MB)

Alien::Build installer class for Module::Build

# SYNOPSIS

In your Build.PL:

    use Alien::Build::MB;
    
    Alien::Build::MB->new(
      module_name => 'Alien::MyLibrary',
      ...
    );

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

    my $abmb = Alien::Build::MB->new(%args);

Takes the usual [Module::Build](https://metacpan.org/pod/Module::Build) arguments.

# METHODS

## alien\_build

    my $build = $abmb->alien_build;

Returns a freshly deserialized instance of [Alien::Build](https://metacpan.org/pod/Alien::Build).  If you make
any changes to this object's `install_prop` or `runtime_prop` properties
be sure that you also call `$build-`checkpoint>!

# ACTIONS

These actions should automatically be called during the normal install
process.  For debugging you may want to call them separately.

## ACTION\_alien\_download

    ./Build alien_download

Downloads the package from the internet.  For a system install this does
not do anything.

## ACTION\_alien\_build

    ./Build alien_build

Build the package from source.

# SEE ALSO

[Alien::Build](https://metacpan.org/pod/Alien::Build), [Alien::Build::MM](https://metacpan.org/pod/Alien::Build::MM), [Alien::Base::ModuleBuild](https://metacpan.org/pod/Alien::Base::ModuleBuild)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
