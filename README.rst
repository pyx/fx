======================================
fx - a functional programming approach
======================================

::

   ___
  |  _|_ _
  |  _|_'_|
  |_| |_,_|igher-order function coding.


Introduction
============

**TL;DR - YAGNI.**

Inspired by `Haskell <http://www.haskell.org/>`_'s rich set of operators,
this is an approach to functional programming with operators in `Python <http://www.python.org/>`_.

  "It's fun... It's insane... It's insanely fun."

  -- John Doe


Features
--------

- Currying functions with ``<<``, ``&``
- Piping output of functions with ``|``
- Composing functions with ``**``
- Flipping order of arguments of function with ``~``
- and more


Examples
--------

::

  >>> from fx import f
  >>> double_all = f(map) << 2 .__mul__ | list
  >>> double_all([1, 2, 3])
  [2, 4, 6]
  >>> double_all |= f(map) << str | ' '.join
  >>> double_all([1, 2, 3])
  '2 4 6'
  >>> sum_upto = 1 .__add__ | f(range) << 1 | sum
  >>> sum_upto(100)
  5050
  >>> parse_hex_str = ~f(int) << 16
  >>> parse_hex_str('ff')
  255
  >>> parse_hex_str('c0ffee')
  12648430
  >>> # project euler problem 1
  >>> euler_p1 = f(range) << 1 | f(filter) << (lambda n: n % 3 == 0 or n % 5 == 0) | sum
  >>> euler_p1(10)
  23
  >>> euler_p1(1000)
  233168
  >>> # project euler problem 20
  >>> fact = f(lambda n: 1 if n == 1 else n * fact(n - 1))
  >>> euler_p20 = str ** fact | sum ** f(map) << int
  >>> euler_p20(10)
  27
  >>> euler_p20(100)
  648


Requirements
============

- CPython >= 2.6


Installation
============

Install from PyPI::

  pip install fx

Install from source, download source package, decompress, then ``cd`` into source directory, run::

  make install


License
=======

BSD New, see LICENSE for details.


Links
=====

Documentation:
  http://fx.readthedocs.org/

Issue Tracker:
  https://bitbucket.org/pyx/fx/issues/

Source Package @ PyPI:
  http://pypi.python.org/pypi/fx/

Mercurial Repoistory @ bitbucket:
  https://bitbucket.org/pyx/fx/

Git Repoistory @ Github:
  https://github.com/pyx/fx/
