# Building / Updating FreeNAS Corral

## Build Guide

Detailed instructions for building FreeNAS can be found [here](https://github.com/freenas/corral-build/wiki/FreeNAS-9.10---10-—-Setting-up-a-FreeNAS-build-environment).

The steps below are the short summary version.

## Requirements

* Operating System
  * For building FreeNAS Corral, your build environment must be FreeBSD 11.0-RELEASE or later.

* Free space
  * For building on a ZFS based system, you must have ~140GB space free.
  * For building on a UFS based system, you must have ~180GB space free.

* An amd64 capable processor.  32GB of memory, or an equal/greater amount
  of swap space, is also required.

* An internet connection for downloading source and packages

## Building FreeNAS

Note: All these commands must be run as `root`.

Install the dependencies:

    # make bootstrap-pkgs

Download and assemble the source code:

    # make checkout PROFILE=profile_type

Compile the source, then generate the .ISO:

    # make release PROFILE=profile_type

The valid profile types are "corral" and "corral-stable" (see
the build/profiles directory) to build a nightly from the master branch or a stable build from the stable branch, respectively.
Instead of specifying PROFILE=profile_type, you can also set the profile type in the file build/profiles/profile-setting
(e.g. ```echo corral > build/profiles/profile-setting```).

Once the build completes successfully, you'll have release bits in the _BE
directory. :smile:

## Updating an existing installation

To update an existing FreeNAS Corral instance that you are using for development
purposes:

* ```make update```
* ```make ports```
* ```make reinstall-package package=freenas host=root@1.2.3.4```

Where 1.2.3.4 is the IP address of your development platform.  SSH will be
used to push and install the new packages onto that host.  (Note previous
comment about setting the profile).  PLEASE NOTE that this is an advanced
development technique and may completely destroy your system if you don't know
what you're doing.
