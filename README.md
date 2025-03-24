# OS Notes

This is a repo for me to write notes in right now. That's it.

## Tech Stack
* Build in Rust. Why?
    * Rust has great memory safety features
    * I like Rust

## Features

### Shell
* Use an existing scripting language, probably Python, as the shell lang. Why?
    * Devs are familiar with Python.
    * LOADS of documentation on Python already
    * Easy to script in (Bash sucks to script in)
    * Don't need to develop one of my own

### Core Utils
* The core utils should be libraries with language bindings first, not programs first. Take `grep`, for example. `grep` would be a lib that can be imported by an application developer's application. If a user wanted to use it in the shell, the shell language would just import `grep` as a part of the prelude and the user would have access to it as soon as they open a terminal window. *Core utils function more as libraries, not programs.*
* `PATH` would not need to exist. Rather than looking for the program in the many `PATH` dirs, the shell lang would know it exists because the util is included in the prelude.

### Application Runtime
Applications would be sandboxed by default. Every application has access to it's own virtual filesystem that is persisted. This prevents malicious software from sharing data with privacy-sensitive software. If an application *does* need to share data with another application, well, idk yet...
