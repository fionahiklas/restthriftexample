## Overview

First code written in go

## Setup

### Structure

I think I've probably made things more complicated than then need to be - I have a git repo for the GOPATH structure and then this repo is 
mounted under that.  This is waaaaayyyy more complex than it needs to be.

One interesting thing is that I have another Go base directory for third party utilities, ~/wd/3rdparty/gobase and I've added that into 
the GOPATH like this

```
export GOPATH=~/wd/fionahiklas/simple_rest_and_thrift_gobase:~/wd/3rdparty/gobase
export PATH=$PATH:~/wd/3rdparty/gobase/bin
``` 

### Dep setup

Ran the following to get things started

```
dep init
```

This created the Gopkg.* files


## Useful Information

### Go Packages

This confused the hell out of me!  I'm not 100% certain I've got it right yet but here is my current mental model

* Go expects everything under a given point in the tree, e.g. github.com/fionahiklas/restthriftexample to belong to either 'main' or 'restthriftexample'
* It seems that a Go package is either an executable OR a library you can't mix code that does both into the same directory
* For example the dep tool (which I'm using) has it's dep library code in the github.com/golang/dep directory (and dep package) but the executable in cmd/dep 
* If you mix up the packages a little and don't follow the rules you get this kind of error

```
can't load package: package github.com/fionahiklas/restthriftexample: found packages restthriftexample (rest_service.go) and main (simplerestandthrift.go) in /Users/fiona/wd/fionahiklas/gobase/src/github.com/fionahiklas/restthriftexample
```

* Looking at dep again it seems that all the code under github.com/golang/dep/cmd/dep is in the 'main' package 
* That code does import libraries from github.com/golang/dep and github.com/golang/dep/gps and others


