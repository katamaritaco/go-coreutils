# Go coreutils

[![forthebadge](http://forthebadge.com/images/badges/made-with-crayons.svg)](http://forthebadge.com)
[![forthebadge](http://forthebadge.com/images/badges/as-seen-on-tv.svg)](http://forthebadge.com)

This is a port of GNU's coreutils (http://www.gnu.org/software/coreutils/)
that aims to be a drop-in, cross-platform replacement.

**It's currently under development.**

Because it imports from `github.com/EricLagergren/go-gnulib`, and I'm constantly
refactoring, parts could break from day-to-day.

I'd recommend running `go get -u ...` before you file a bug report!

*Pull requests are more than welcome.*

Also, see https://www.github.com/EricLagergren/go-gnulib for a similar project that this project depends on.

### Completed:

16/100

| Utility | Completeness   | Cross Platform      | Need Refactor|
|:--------|:---------------|:--------------------|:-------------|
| cat     | 100%           | Yes (Unix/Windows)  | No           |
| chown   | 10% (* see note #1) | No             | Yes (-R)     |
| env     | 100%           | Yes (Unix/Windows)  | No           |
| false   | 100%           | Yes (Unix/Windows)  | No           |
| logname | 100%           | No                  | No           |
| pwd     | 100%           | Yes (Unknown)       | No           |
| sync    | 100%           | Yes (Unix/Windows)  | No           |
| true    | 100%           | Yes (Unix/Windows)  | No           |
| tsort   | 100%           | Yes (Unix/Windows)  | No           |
| tty     | 100%           | Yes (Unix/Windows)  | No           |
| uname   | 100%           | No                  | No           |
| uptime  | 90%            | Yes (Unix/Window, no FreeBSD)   | No           |
| wc      | 100%           | Yes (Unix/Windows)  | No           |
| whoami  | 100%           | Yes (Unix/Windows   | No           |
| xxd     | 100%           | Yes (Unix/Windows)  | No           |
| yes     | 100%           | Yes (Unix/Windows)  | No           |

* chown note: Currently refactoring from the ground-up.

**Side notes:**
- Unix *should* include OS X unless otherwise specified.
- Gofmt means it needs its styling changes (e.g. variable names, formatting, etc.)
- Idiomatic means it needs to be changed to more idiomatic Go
- Windows coverage will increase when I get a Windows laptop

### Information:

These utilities should be nearly identical to GNU's coreutils, and should have
*relatively* the same speed.

For example, `wc.go` counts chars in 550MB file in < 15sec and `wc.c` in ~11sec
on an Intel core i3 2.66ghz. (Running Debian 3.2.63-2+deb7u1 x86_64.)

`xxd.go` is actually much faster than the native `xxd` implementation found
on most *nix machines -- try it out!

It (as a whole) is licensed under the GPLv3 because it's mostly a
transliteraiton of GNU's coreutils, which are licensed under the GPL.

However, all parts are/can be licensed individually, as **not** all are under
the GPL (e.g., `xxd` was public domain).

## REQUIRES:

(Depends on platform and command...)
- go get github.com/EricLagergren/ostypes
- go get golang.org/x/sys/unix
- go get github.com/ogier/pflag
- go get github.com/EricLagergren/go-gnulib/ttyname
- go get github.com/EricLagergren/go-gnulib/sysinfo
- go get github.com/EricLagergren/go-gnulib/posix
- go get github.com/EricLagergren/go-gnulib/general
- go get github.com/EricLagergren/go-gnulib/login

### LICENSE:

```
   Copyright (C) 2014-2015 Eric Lagergren

   This program is free software: you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation, either version 3 of the License, or
   (at your option) any later version.

   This program is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.

   You should have received a copy of the GNU General Public License
   along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
