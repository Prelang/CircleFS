# Circular File System Concept

## Description

A filesystem (most likely virtual via FUSE) where:

1.) A directory index contains a list of all the (unique) directories and subdirectories in the tree.  Example:

```
~/example
  ./images
  ./mockups
  ./screencasts
```
  
2.) Entering one of the sub-directories will narrow down the files/directories.

```
~/example/mockups
  images-Homepage.psd
  ./images
  Mockups.ppt

~/example/mockups/images
  Homepage.psd
  
~/example/screencasts/images
  Background.psd
```

3.) Those files also exist in any other subdirectory which is part of the path and be prefixed accordingly.

```
~/example/images
  mockups-Homepage.psd
  ./mockups
  screencasts-Background.psd
  ./screencasts

~/example/screencasts
  images-Background.psd
  ./images
  Screencast.mov
```

Thus the contents of `~/examples/images/screencasts` == `~/examples/screencats/images`.

## Why?

### Efficient Overviews
It's inefficient to go digging through sub directories if you have a layout such as this and just want to look at "all images".

```
~/foo
  ./screencats/images
  ./images
```

Instead of inspecting each directory, you could simply see "all images" at `./images`.

### Efficient/Ambiguous Directory Changes

Instead of remembering "my 'screencast image files' are located at `./screencasts/images`" you could change directory into either `./screencasts/images` or `./images/screencasts`.

## Authors

Erik Nomitch and Andrew Yates

Concept by [Erik Nomitch](http://eriknomitch.com)

