# XFileSelect
A simple file select dialog 

![File-selector](https://github.com/brummer10/XFileSelect/raw/master/XFileSelect.png)

## Features

- select a file from a directory and print the filepath/name to stdout.
- filter files to select by extension or by xdg-mime type
- open files with the default application given by 'xdg-open'

## Usage

xfileselect [args]
camandline args:
-   [-p path] optional set a path to open
-   [-f filter] optional set a file filter, were a filter could be any of the xdg-mime typs, or a file extension including the dot.
-   [-x ] optional open file with xdg-open

all commandline args been optional. 

## Dependencys

- libcairo2-dev
- libx11-dev

## Build
- git submodule init
- git submodule update
- make

that's it.
