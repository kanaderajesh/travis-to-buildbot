# travis-to-buildbot
<div>
<p>The objective of this project is to convert any given travis build to buildbot build, travis will be parsed and
converted to a config file understood by buildbot.</p>
<pre>
Below is the sample .travis.yml file
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

</pre>
</div>
