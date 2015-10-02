# makedepfort

## Introduction

This is a small Python script to extract the prerequisites of
the object file that is obtained by compiling a fortran source
file named on the command line.  The results are printed in the
format that is used in makefiles' dependency lists.

There are several tools which do the same thing, namely,

* [makedepf90](http://personal.inet.fi/private/erikedelmann/makedepf90/)
* [sfmakedepend](http://marine.rutgers.edu/po/tools/perl/sfmakedepend)
* [f90_mod_deps.py](http://lagrange.mechse.illinois.edu/partmc/partmc-1.1.0/tool/f90_mod_deps.py)
(c.f. the information found [here](http://lagrange.mechse.illinois.edu/f90_mod_deps/) is very valuable.)

but none of them satisfied the author; for example, for some files
makedepf90 falls into infinite loops.  Therefore, he decided to
make it by himself.

## Installation
At present there's no setup.py install script; place this script
somewhere PATH environmental variable points (additionaly you may
adjust the first line which reads `#!/usr/bin/env python` to your
environment).

## Usage
```
usage: makedepfort [-h] [-g] ffile [ffile ...]

positional arguments:
  ffile

optional arguments:
  -h, --help            show this help message and exit
  -g, --include-global  include dependencies on global include files
```

The usage shown above is printed by `makedepfort -h`.

## Features and Limitation

* By default, this script does not list the include files which are
not found by searching for the files using the paths specified in
the source files; these shoud be in some *standard directories*.
  Use options `-g` or `--include-global` to list these include files.

* At this moment the extention for module files is fixed to `.mod`;
it is not difficult to add an option for this.

## License
This is free software; it can be copied, used, modified and
redistributed under the terms of the GNU Lesser General Public License
version 2.  You can read it in the LICENSE file which should be
distributed with the software, or [its web site](http://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html).
