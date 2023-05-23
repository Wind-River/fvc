# File Verification Code
A File Verification Code is used to identify a collection of files.
The same collection of files, whether in a directory, a zip, a tar, or any other form, generates the same file verification code.

## FVC Version 2 Algorithm
1. Collect sha256, in raw bytes, of every regular file in the collection
    - Any irregular files, including symlinks, named pipes, sockets, block devices, and charcater devices, are entirely ignored
    - Any sub-archives encountered should be extracted and their contents similarily added to the list, the sub-archive's own sha256 is not included
    - Any quine, an archive that extracts into itself, should not be allowed to recurse
2. Sort this list of sha256s
3. Calculate sha256 of this list
4. Prepend 'FVC2' and null to the sha256 of the list

## Implementations
We have sample implementation libraries and cli utilites that use these libraries in Golang and Rust.
- [Golang](https://github.com/Wind-River/fvc-go)
- [Rust](https://github.com/Wind-River/fvc-rs)