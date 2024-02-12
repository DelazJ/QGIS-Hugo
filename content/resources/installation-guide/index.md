---
type: "page"
title: "Installation Guide"
subtitle: ""
draft: false
sidebar: true
---

{{< content-start  >}}

# QGIS Installers

How to obtain QGIS?

QGIS is available on Windows, macOS, Linux, Android and iOS.

We recommend installing the packages of the released software.

To evaluate the upcoming release and to allow non-developers to support development we also provide testing packages (note the [warning](https://qgis.org/en/site/forusers/alldownloads.html#warning)).

In the feature frozen phase preceding a release (see [Release schedule](https://qgis.org/en/site/getinvolved/development/roadmap.html#qgis-release-schedule)) these packages are effectively **pre-releases, which we strongly urge users to test**.

# Windows

There are two options for installations on Windows:

## Standalone installers

For beginners the easiest way is using the standalone installers:

|Release|Version|Package|
|---|---|---|
|Latest Release|3.34.3 Prizren ​|[Installer](https://qgis.org/downloads/QGIS-OSGeo4W-3.34.3-1.msi) [Checksum](https://qgis.org/downloads/QGIS-OSGeo4W-3.34.3-1.sha256sum)|
|Long Term Release|3.28.15 Firenze LTR|[Installer](https://qgis.org/downloads/QGIS-OSGeo4W-3.28.15-1.msi) [Checksum](https://qgis.org/downloads/QGIS-OSGeo4W-3.28.15-1.sha256sum)|
|Development|3.35 master|[Weekly snapshots](https://download.osgeo.org/qgis/windows/weekly/?C=M&O=D)|

See also [The main installers page](https://qgis.org/en/site/forusers/download.html).

The weekly snapshots of the nightly qgis-dev package of OSGeo4W are for users that cannot use OSGeo4W (see below) for some reason or just prefer standalone installers. In the feature freeze phase that also acts as **release candidate**.

## OSGeo4W installer

More advanced QGIS users should use OSGeo4W packages, which for one make it possible to install several versions in parallel and also to do much more efficient updates as only changed components are downloaded and installed.

The OSGeo4W repository contains a lot of software from OSGeo projects. QGIS and all dependencies are included, along with Python, GRASS, GDAL, etc. The installer is able to install from internet or just download all needed packages beforehand. The downloaded files are kept in a local directory for future installations and could also be used to install offline.

Steps are:

- Download [OSGeo4W Installer](https://download.osgeo.org/osgeo4w/v2/osgeo4w-setup.exe) and start it
    
- Choose _Express Install_ and select _QGIS_ to install the _latest release_ and/or _QGIS LTR_ to install the _long term release_.
    

Alternatively to _Express_ you also use the _Advanced Install_, navigate to the _Desktop_ section and pick one or more of the following packages:

|Release|Version|Package|Description|
|---|---|---|---|
|Latest Release|3.34.3 Prizren ​|qgis|Release|
|qgis-rel-dev [[1]](https://qgis.org/en/site/forusers/alldownloads.html#id5)|Nightly build of the upcoming point release|
|Long Term Release|3.28.15 Firenze LTR|qgis-ltr|Release|
|qgis-ltr-dev [[1]](https://qgis.org/en/site/forusers/alldownloads.html#id5)|Nightly build of the upcoming long term point release|
|Development|3.35 master|qgis-dev [[1]](https://qgis.org/en/site/forusers/alldownloads.html#id5)|Nightly build of the development version|

[1] ([1](https://qgis.org/en/site/forusers/alldownloads.html#id2),[2](https://qgis.org/en/site/forusers/alldownloads.html#id3),[3](https://qgis.org/en/site/forusers/alldownloads.html#id4))

Nightlies are debug builds (including debugging output)

The packages listed in the table only install the necessary packages to run QGIS. Corresponding to those packages there are also meta packages with the postfix `-full-free` and `-full`. The former contains additional optional dependencies that some popular - not included - plugins use and the latter include the former and also add proprietary extensions like Oracle, ECW and MrSID.

The Express installs reference the corresponding `-full` variant and the standalone installers are also made from these OSGeo4W package sets.

Before installing any of the nightly builds note the [warning](https://qgis.org/en/site/forusers/alldownloads.html#warning).

# Linux

Most linux distributions split QGIS into several packages; you’ll probably need qgis and qgis-python (to run plugins). Packages like qgis-grass (or qgis-plugin-grass), qgis-server can be skipped initially, or installed only when you need them.

Below you find instructions to install per distribution. For most distro’s there are instructions to install QGIS stable and instructions to install a cutting edge QGIS testing build (note the [warning](https://qgis.org/en/site/forusers/alldownloads.html#warning)).

## Debian/Ubuntu

### Quickstart

Note

In the section following this one, you will find ALL possible options to install different versions of QGIS in different versions of Debian/Ubuntu. If you have problems, verify there whether your distribution is still supported as the repositories also contain older **unsupported** distributions with the last QGIS version that was supported. Beware that those might have meanwhile ceased to work.

Here you will simply install the latest stable QGIS (3.34.x Prizren) in your Debian or Ubuntu without having to edit config files.

Note

Although you see ‘Debian’ in some places, this also works for ‘Ubuntu’, as one is actually a symlink to the other on our server.

First install some tools you will need for this instructions:

```
sudo apt install gnupg software-properties-common
```

Now install the QGIS Signing Key, so QGIS software from the QGIS repo will be trusted and installed:

```
sudo mkdir -m755 -p /etc/apt/keyrings  # not needed since apt version 2.4.0 like Debian 12 and Ubuntu 22 or newer
sudo wget -O /etc/apt/keyrings/qgis-archive-keyring.gpg https://download.qgis.org/downloads/qgis-archive-keyring.gpg
```

Add the QGIS repo for the latest stable QGIS (3.34.x Prizren) to `/etc/apt/sources.list.d/qgis.sources`:

```
Types: deb deb-src
URIs: https://qgis.org/debian
Suites: your-distributions-codename
Architectures: amd64
Components: main
Signed-By: /etc/apt/keyrings/qgis-archive-keyring.gpg
```

Note

`Suites` in above lines depends on your distribution. `lsb_release -cs` will show your distribution name.

In some distributions (like Linux Mint), `. /etc/os-release; echo "$UBUNTU_CODENAME"` will show the correct distibution name.

See [Available codenames](https://qgis.org/en/site/forusers/alldownloads.html#available-codenames).

Update your repository information to reflect also the just added QGIS one:

```
sudo apt update
```

Now, install QGIS:

```
sudo apt install qgis qgis-plugin-grass
```

Note

Add `qgis-server` to this line if you also want to install QGIS Server

### Repositories

Default Debian and Ubuntu software repositories often hold older versions of QGIS.

To have newer versions, you have to add alternative software repositories, by adding one of the deb-lines below to your `/etc/apt/sources.list.d/qgis.sources` file.

Our main repository contains multiple lines of packages for several versions of **Debian and Ubuntu** based on the dependencies the individual distributions provide.

For Ubuntu we also used to have extra packages in a separate repository that are based on [ubuntugis](https://launchpad.net/~ubuntugis), which held more uptodate versions of other GIS packages than Ubuntu itself for LTS versions. If you want those you also need to include ubuntugis-unstable ppa in your /etc/apt/sources.list.d/qgis.list file (see [ubuntugis documentation](https://trac.osgeo.org/ubuntugis/wiki/UbuntuGISRepository)).

Note

The release packages are only produced once shortly after a new version has been released. As unstable, not yet released debian versions (testing) and ubuntugis-unstable can have library changes the packages might sooner or later be broken for these targets, when the development in debian, ubuntu or ubuntugis-unstable moves on and their packages used as dependencies in qgis change. In that event you can either

- move to a stable debian version and use the released packages for it,
    
- wait for the next point release (due 2024-02-23 12:00:00 UTC), which happens every month and will include the updated dependencies,
    
- switch to a nightly repository (available for the **two** release branches and master) whose packages are rebuild on regular basis and will also pickup the updated dependencies automatically or
    
- build your own set of packages (see [build-debian-packages](https://github.com/qgis/QGIS/blob/master/INSTALL.md#310-building-debian-packages)).
    

Lines of packages:

| Release | Version | Description | Repository |
| ---- | ---- | ---- | ---- |
| Latest Release | 3.34.x Prizren ​ | Release for **Debian and Ubuntu** | [https://qgis.org/debian](https://qgis.org/debian) [https://qgis.org/ubuntu](https://qgis.org/ubuntu) |
| Release with ubuntugis-unstable dependencies | [https://qgis.org/ubuntugis](https://qgis.org/ubuntugis) |  |  |
| Nightly build of upcoming point release for Debian and Ubuntu [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/debian-nightly-release](https://qgis.org/debian-nightly-release) [https://qgis.org/ubuntu-nightly-release](https://qgis.org/ubuntu-nightly-release) |  |  |
| Nightly build of upcoming point release with ubuntugis-unstable dependencies [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/ubuntugis-nightly-release](https://qgis.org/ubuntugis-nightly-release) |  |  |
| Long Term Release Repository | 3.28.x Firenze LTR | Release for **Debian and Ubuntu** | [https://qgis.org/debian-ltr](https://qgis.org/debian-ltr) [https://qgis.org/ubuntu-ltr](https://qgis.org/ubuntu-ltr) |
| Release with ubuntugis-unstable dependencies | [https://qgis.org/ubuntugis-ltr](https://qgis.org/ubuntugis-ltr) |  |  |
| Nightly build of upcoming point release for Debian and Ubuntu [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/debian-nightly-ltr](https://qgis.org/debian-nightly-ltr) [https://qgis.org/ubuntu-nightly-ltr](https://qgis.org/ubuntu-nightly-ltr) |  |  |
| Nightly build of upcoming point release with ubuntugis-unstable dependencies [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/ubuntugis-nightly-ltr](https://qgis.org/ubuntugis-nightly-ltr) |  |  |
| Development Version | 3.35 master | Nightly build for **Debian and Ubuntu** [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/debian-nightly](https://qgis.org/debian-nightly) [https://qgis.org/ubuntu-nightly](https://qgis.org/ubuntu-nightly) |
| Nightly build with ubuntugis-unstable dependencies [[5]](https://qgis.org/en/site/forusers/alldownloads.html#id12) | [https://qgis.org/ubuntugis-nightly](https://qgis.org/ubuntugis-nightly) |  |  |

[5] ([1](https://qgis.org/en/site/forusers/alldownloads.html#id6),[2](https://qgis.org/en/site/forusers/alldownloads.html#id7),[3](https://qgis.org/en/site/forusers/alldownloads.html#id8),[4](https://qgis.org/en/site/forusers/alldownloads.html#id9),[5](https://qgis.org/en/site/forusers/alldownloads.html#id10),[6](https://qgis.org/en/site/forusers/alldownloads.html#id11))

nightlies are debug builds (including debug output)

Next point release: 2024-02-23 12:00:00 UTC

Next release: 2024-02-23 12:00:00 UTC

(more dates see Release Schedule on [Road Map](https://qgis.org/en/site/getinvolved/development/roadmap.html))

Supported distribution versions:

|Distribution|Version|Codename|Also available based on ubuntugis-unstable dependencies?|
|---|---|---|---|
|Debian|12.x (stable)|bookworm||
|11.x (oldstable)|bullseye||
|unstable|sid||
|Ubuntu|24.04 (LTS) [[6]](https://qgis.org/en/site/forusers/alldownloads.html#id14)|noble||
|23.10|mantic||
|23.04|lunar||
|22.04 (LTS)|jammy|yes|

[[6](https://qgis.org/en/site/forusers/alldownloads.html#id13)]

future ubuntu release planned for 2024-04-25

To use the qgis archive you have to first add the archive’s repository public key:

```
wget https://download.qgis.org/downloads/qgis-archive-keyring.gpg
gpg --no-default-keyring --keyring ./qgis-archive-keyring.gpg --list-keys
```

Should output:

```
./qgis-archive-keyring.gpg
--------------------------
pub   rsa4096 2022-08-08 [SCEA] [expires: 2027-08-08]
      2D7E3441A707FDB3E7059441D155B8E6A419C5BE
uid           [ unknown] QGIS Archive Automatic Signing Key (2022-2027) <qgis-developer@lists.osgeo.org>
```

After you have verified the output you can install the key with:

```
sudo mkdir -m755 -p /etc/apt/keyrings  # not needed since apt version 2.4.0 like Debian 12 and Ubuntu 22 or newer
sudo cp qgis-archive-keyring.gpg /etc/apt/keyrings/qgis-archive-keyring.gpg
```

Alternatively you can download the key directly without manual verification:

```
sudo mkdir -m755 -p /etc/apt/keyrings  # not needed since apt version 2.4.0 like Debian 12 and Ubuntu 22 or newer
sudo wget -O /etc/apt/keyrings/qgis-archive-keyring.gpg https://download.qgis.org/downloads/qgis-archive-keyring.gpg
```

With the keyring in place you can add the repository as `/etc/apt/sources.list.d/qgis.sources` with following content:

```
Types: deb deb-src
URIs: *repository*
Suites: *codename*
Architectures: amd64
Components: main
Signed-By: /etc/apt/keyrings/qgis-archive-keyring.gpg
```

Example for the latest long term release for Ubuntu 22.04 Jammy:

```
Types: deb deb-src
URIs: https://qgis.org/ubuntu-ltr
Suites: jammy
Architectures: amd64
Components: main
Signed-By: /etc/apt/keyrings/qgis-archive-keyring.gpg
```

After that type the commands below to install QGIS:

```
sudo apt update
sudo apt install qgis qgis-plugin-grass
```

In case you would like to install QGIS Server, type:

```
sudo apt update
sudo apt install qgis-server --no-install-recommends --no-install-suggests
# if you want to install server Python plugins
apt install python3-qgis
```

Note

Please remove all the QGIS and GRASS packages you may have installed from other repositories before doing the update.

## Fedora

Get packages for any Fedora by typing:

```
sudo dnf install qgis python3-qgis qgis-grass qgis-server
```

Default Fedora software repositories often hold older versions of QGIS.

To have newer versions or the latest LTR, you have to add alternative software repositories based on the version you want to install (stable, LTR or testing).

### QGIS stable

Enable the repository:

```
sudo dnf copr enable dani/qgis
```

After that type the commands below to install QGIS:

```
sudo dnf install qgis python3-qgis qgis-grass
```

In case you would like to install QGIS Server (note that it’s not a common practice to install both client and server applications on the same machine), type:

```
sudo dnf install qgis-server python3-qgis
```

|Distribution|Version|QGIS version|GRASS GIS version|
|---|---|---|---|
|Fedora|36|3.28|8.0|
|37|3.28|8.2|

More information are available at [https://copr.fedorainfracloud.org/coprs/dani/qgis/](https://copr.fedorainfracloud.org/coprs/dani/qgis/)

### QGIS LTR (Long Term Release)

Enable the repository:

```
sudo dnf copr enable dani/qgis-ltr
```

After that type the commands below to install QGIS:

```
sudo dnf install qgis python3-qgis qgis-grass
```

In case you would like to install QGIS Server (note that it’s not a common practice to install both client and server applications on the same machine), type:

```
sudo dnf install qgis-server python3-qgis
```

|Distribution|Version|QGIS version|GRASS GIS version|
|---|---|---|---|
|Fedora|36|3.22|8.0|
|37|3.22|8.2|

More information are available at [https://copr.fedorainfracloud.org/coprs/dani/qgis-ltr/](https://copr.fedorainfracloud.org/coprs/dani/qgis-ltr/)

## SUSE / openSUSE

Latest stable and LTR packages called qgis and qgis-ltr are available in the following repositories:

|Distribution|Repository|
|---|---|
|Tumbleweed|[https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Tumbleweed/](https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Tumbleweed/)|
|Leap 15.2|[https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Leap_15.2/](https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Leap_15.2/)|
|Leap 15.1|[https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Leap_15.1/](https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Leap_15.1/)|
|Factory ARM|[https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Factory_ARM/](https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Factory_ARM/)|
|Factory PowerPC|[https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Factory_PowerPC/](https://download.opensuse.org/repositories/Application:/Geo/openSUSE_Factory_PowerPC/)|
|SLE 15 SP1 Backports|[https://download.opensuse.org/repositories/Application:/Geo/SLE_15_SP1_Backports/](https://download.opensuse.org/repositories/Application:/Geo/SLE_15_SP1_Backports/)|
|SLE 15 SP1 Backports debug|[https://download.opensuse.org/repositories/Application:/Geo/SLE_15_SP1_Backports_debug/](https://download.opensuse.org/repositories/Application:/Geo/SLE_15_SP1_Backports_debug/)|

All packages include GRASS and Python support.

All openSUSE Geo repositories can be found here: [https://download.opensuse.org/repositories/Application:/Geo/](https://download.opensuse.org/repositories/Application:/Geo/)

## Mandriva

### QGIS stable

Current:

```
urpmi qgis-python qgis-grass
```

## Slackware

### QGIS stable

Packages on [https://slackbuilds.org/result/?search=qgis](https://slackbuilds.org/result/?search=qgis)

## Arch Linux

### QGIS stable

Arch Linux is available in official repository : [https://archlinux.org/packages/extra/x86_64/qgis/](https://archlinux.org/packages/extra/x86_64/qgis/)

Install with:

```
pacman -S qgis
```

### QGIS LTR

QGIS Long Term Release is available in AUR (Arch User Repository).

Install with yaourt or other package manager which support AUR:

```
yaourt -S qgis-ltr
```

For bugs and other behaviour, read comments here : [https://aur.archlinux.org/packages/qgis-ltr/](https://aur.archlinux.org/packages/qgis-ltr/)

### QGIS testing

QGIS testing is available in AUR (Arch User Repository).

Install with yaourt or other package manager which support AUR:

yaourt -S qgis-git

For bugs and other behaviour, read comments here : [https://aur.archlinux.org/packages/qgis-git](https://aur.archlinux.org/packages/qgis-git)

## Flatpak

There is an QGIS flatpak for QGIS Stable available, maintained by the flathub community.

For general Linux Flatpak install notes, see [https://flatpak.org/setup/](https://flatpak.org/setup/)

QGIS on Flathub: [https://flathub.org/apps/details/org.qgis.qgis](https://flathub.org/apps/details/org.qgis.qgis)

To install:

```
flatpak install --from https://dl.flathub.org/repo/appstream/org.qgis.qgis.flatpakref
```

Then to run:

```
flatpak run org.qgis.qgis
```

To update your flatpak QGIS:

```
flatpak update
```

On certain distributions, you may also need to install xdg-desktop-portal or xdg-desktop-portal-gtk packages in order for file dialogs to appear.

Flathub files: [https://github.com/flathub/org.qgis.qgis](https://github.com/flathub/org.qgis.qgis) and report issues here: [https://github.com/flathub/org.qgis.qgis/issues](https://github.com/flathub/org.qgis.qgis/issues)

Note: if you need to install additional Python modules, because they are needed by a plugin, you can install the module with (here installing the scipy module):

flatpak run --devel --command=pip3 org.qgis.qgis install scipy --user

## Spack

Spack is a distro agnostic package manager for Linux, which is developed in the context of high-performance computing.

General info on installing Spack: [https://github.com/spack/spack](https://github.com/spack/spack)

QGIS package file on Spack: [https://github.com/spack/spack/blob/develop/var/spack/repos/builtin/packages/qgis/package.py](https://github.com/spack/spack/blob/develop/var/spack/repos/builtin/packages/qgis/package.py)

To install:

```
spack install qgis
```

which builds and installs QGIS and **all** dependencies from scratch. Afterwards, QGIS can be used via:

```
spack load qgis
```

If additional python packages need to be installed, using a Spack environment is recommended. For example:

```
spack env create myenv
spack env activate -p myenv
spack add qgis py-lz4
spack install
```

Spack related issues should be reported at: [https://github.com/spack/spack/issues](https://github.com/spack/spack/issues)

# Mac OS X / macOS

Official All-in-one, signed installers for macOS High Sierra (10.13) and newer can be downloaded from the [QGIS download page](https://qgis.org/en/site/forusers/download.html).

## QGIS nightly release

A nightly updated standalone installer from QGIS master can be downloaded from [here](https://qgis.org/downloads/macos/qgis-macos-nightly.dmg).

## MacPorts

The package management system [MacPorts](https://www.macports.org) offers both the latest release version (port `qgis3`) and the long term version (port `qgis3-ltr`). This will install QGIS with native architecture, Intel x86_64 or Apple ARM. Main software dependencies such as GDAL, PDAL and GRASS GIS are usually the latest version available.

[Installing MacPorts and updating](https://guide.macports.org) it and the _ports_ are made with the _Terminal_. QGIS is however installed as an app bundle at `/Applications/MacPorts/QGIS3.app`.

Get information of a port:

```
sudo port info qgis3
```

Install port, e.g with GRASS GIS:

```
sudo port install qgis3 +grass
```

Update:

```
sudo port selfupdate
sudo port upgrade outdated
```

Note

Concurrent installation of Homebrew and MacPorts is not compatible and will almost certainly lead to conflicts. If you choose to install one of the package systems you need to uninstall the other.

## Old releases

Previous releases of the official installer can be downloaded from [https://qgis.org/downloads/macos/](https://qgis.org/downloads/macos/).

Previous releases of the kyngchaos installer can be downloaded from [https://www.kyngchaos.com/software/archive/qgis/](https://www.kyngchaos.com/software/archive/qgis/). The oldest installers support macOS 10.4 Tiger.

# FreeBSD

## QGIS stable

To install QGIS from binary packages type

```
pkg install qgis
```

Or to customize compilation options, you can build it from FreeBSD ports

```
cd /usr/ports/graphics/qgis
make install clean
```

## QGIS LTR

To install QGIS from binary packages type

```
pkg install qgis-ltr
```

Or to customize compilation options, you can build it from FreeBSD ports

```
cd /usr/ports/graphics/qgis-ltr
make install clean
```

# OpenBSD

QGIS Stable

To install QGIS from third-party package

```
pkg_add qgis
```

See: - [https://openbsd.app/?search=qgis](https://openbsd.app/?search=qgis) # for -stable OpenBSD - [https://openbsd.app/?search=qgis&current=on](https://openbsd.app/?search=qgis&current=on) # for -current OpenBSD

# Android

An old and deprecated not touch optimised release of QGIS for Android can be found on the google play store.

[https://play.google.com/store/apps/details?id=org.qgis.qgis](https://play.google.com/store/apps/details?id=org.qgis.qgis)

Warning

There is currently no support for Android 5. Best support is given for Android 4.3 and 4.4.x. This is a direct port of the QGIS desktop application. It is only slightly optimized for touch devices and therefore needs to be carefully evaluated for its suitability in day-to-day use. There are other apps available which are designed and optimized specifically for touch devices.

# QGIS Testing warning

Warning

QGIS testing packages are provided for some platforms in addition to the QGIS stable version. QGIS testing contains unreleased software that is currently being worked on. They are only provided for testing purposes to early adopters to check if bugs have been resolved and that no new bugs have been introduced. Although we carefully try to avoid breakages, it may at any given time not work, or may do bad things to your data. Take care. You have been warned!

# Installing from Source

Refer to [INSTALL](https://github.com/qgis/QGIS/blob/master/INSTALL.md) on how to build and install QGIS from source for the different platforms.

{{< content-end >}}