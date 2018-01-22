# pip-eclass
provide python way to install package for gentoo

# About pip-r1.class
I just hate the way installing python package in gentoo, especially when I have to add a link to SRC_URI with hash string. that looks ugly.
pip-r1.class still following the rules gentoo package installation, it just make writing a python package ebuild easier ( maybe :) ).
pip-r1.class install python package via pip, but only one package one time, you have to deal with package dependency yourself. 

# How to use?
```
EAPI=5 # or 6
PYTHON_COMPAT=( python{2_7,3_{4,5,6}} )
inherit pip-r1

# PY_INDEX="https://pypi.python.org/pypi/face_recognition" # if pip couldn't find package in default trunk, then try this link first
PY_PN=${PN//-/_} # if this var defined, pip use the var for searching package directly. otherwise, still PN
# PY_PV # same as above

DESCRIPTION="Recognize faces from Python or from the command line"
HOMEPAGE="https://pypi.python.org/pypi/face_recognition" # if pip couldn't find package in PY_INDEX stll, this is the last try

# for some packages not following pip rules, you still can specify download link in SRU_URI. but mind the order if there's multiple links, links order must be same as PYTHON_COMPAT
# SRC_URI="link-for-python2.7
#	link-for-python3.4
#	link-for-python3.5
#	link-for-python3.6
# " 
```

# TODO
custom configuration via use flags
patching?
