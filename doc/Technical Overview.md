# File Management

## On File Created

If `~/foo` is a CircleFS-mounted directory and a user changes directories into `~/foo/images/mockups` and creates `Homepage.psd` there:
1. The tags are parsed from the relative path from `~/foo` (i.e., `images`, `mockups`)
2. Since these subdirectories already existed, the *tags* already existed as well. The tags are alphabetized and `Homepage.psd` is filed away in the source directory via a hash blob.

Conversely, if a user changes directories into `~/foo/images/mockups` and makes a new directory `exports` and it does not exist within the tree, CircularFS creates a new tag `exports`.
