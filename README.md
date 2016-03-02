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
    - cmake
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
<p> from the above script, this project will generate script similar to the one mentioned below.</p>
<pre>
  from buildbot.plugins import util, steps
  f = util.BuildFactory()
  f.addStep(steps.ShellCommand(command=["apt-get", "install","cmake"]))
  f.addStep(steps.ShellCommand(command=["cd", "build"]))
  f.addStep(steps.ShellCommand(command=["rm", "-Rf", "*"]))
  f.addStep(steps.ShellCommand(command=["cmake", ".."]))
  f.addStep(steps.ShellCommand(command=["make"]))
</pre>

</div>
