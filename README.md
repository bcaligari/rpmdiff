# rpmdiff

Takes two lists of RPMs and reports on version differences.

Copyright (c) 2020-2021 Brendon Caligari <caligari@cypraea.co.uk>

    License: GNU Affero General Public License
        https://www.gnu.org/licenses/agpl-3.0.en.html

## Use cases

* Checking package differences between two cluster nodes.
* Checking packages differences between a node and a baseline.

## Usage

```{text}
    usage: rpmdiff [-h] rpmlist0 rpmlist1

    Version diff between two lists of RPMs

    positional arguments:
      rpmlist0    A list of RPMs
      rpmlist1    A second list of RPMs

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
```

The list of RPMs can be:

* The output of `rpm -qa`.
* TODO: A supportconfig archive.
* TODO: An expanded supportconfig directory.
* The `rpm.txt` from a supportconfig archive.

### Examples

#### Show only mismatches

```{text}
rpmdiff scc_ha12sp5a_211111_2319 scc_ha12sp5b_211111_2320 2> /dev/null | grep -v '^.='
```

## Observations

* Will hopefully work on openSUSE 15.3 or later with included Python 3.
* Limited error checking is done because it expects one to know what they're
  doing.
