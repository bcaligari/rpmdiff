# rpmdiff

Takes two lists of RPMs and reports on version differences.

Copyright (c) 2020-2021 Brendon Caligari <caligari@cypraea.co.uk>

    License: GNU Affero General Public License
        https://www.gnu.org/licenses/agpl-3.0.en.html

## Usage

    usage: rpmdiff [-h] rpmlist0 rpmlist1

    Version diff between two lists of RPMs

    positional arguments:
      rpmlist0    An output of 'rpm -qa', or 'rpm.txt' from supportconfig
      rpmlist1    Another output of 'rpm -qa', or 'rpm.txt' from supportconfig

    optional arguments:
      -h, --help  show this help message and exit

    Legend:
      ++   present in first but not second
      --   present in second but not first
      ==   present in both at same revision
      <<   version in first lower than one in second
      >>   version in first higher than one in second
      :+   multiversion install present in first but not second
      :-   multiversion install present in second but not first
      :=   multiversion install present in both
