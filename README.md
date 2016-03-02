# travis-to-buildbot
<div>
<p>The objective of this project is to convert any given travis build to buildbot build, travis will be parsed and
converted to a config file understood by buildbot.</p>
<article>
Below is the sample .travis.yml file
# .travis.yml - Travis CI service confiuration for GEOS
#
#
# This is free software; you can redistribute and/or modify it under
# the terms of the GNU Lesser General Public Licence as published
# by the Free Software Foundation.
# See the COPYING file for more information.
#

os:
    - linux

sudo: false

language: cpp

compiler:
    - g++

env:

matrix:
  fast_finish: true
  allow_failures:

addons:
  apt:
    packages:
    - gcc-multilib
    - g++-multilib
    - cmake
    - make
    - make test

script:
    - cd build
    - rm -Rf *
    - cmake ..
    - make

notifications:
    email:
        recipients:
           kanaderajesh@gmail.com
        on_success: change
        on_failure: always

</article>
</div>
