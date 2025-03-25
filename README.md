# OS Notes

This is a repo for me to write notes in right now. That's it.

## Development
* Build in Rust. Why?
    * Rust has great memory safety features
    * I like Rust
* Open source
    * Trust with privacy
    * The open source community can help and will need to, if this project becomes anything at all. The amount of dev time required to ship an OS is massive. There is not much money in consumer-first desktop OSes. Funding this project privately would be next to impossible.
    * There is *no* competition for a mainstream open source desktop OS that is all managed under one roof. (Linux/GNU/GUI is too fragmented)
* Use the [tracer-bullet method](https://www.barbarianmeetscoding.com/notes/books/pragmatic-programmer/tracer-bullets/) for development. This is coined (I think) from the book, The Pragmatic Programmer, by Andy Hunt and Dave Thomas. Basically, the OS will be built in working shape as soon as possible, but with only the features necessary to make it "work". New features will be built out at time goes on. This allows stakeholders to see progress very early on and gives early experimenters something to get their hands on early.

## Features

### Shell
* Use an existing scripting language, probably Python (maaaaybe Lua), as the shell lang. Why?
    * Devs are familiar with Python.
    * LOADS of documentation on Python already
    * Easy to script in (Bash sucks to script in)
    * Don't need to develop one of my own

### Core Utils
* The core utils should be libraries with language bindings first, not programs first. Take `grep`, for example. `grep` would be a lib that can be imported by an application developer's application. If a user wanted to use it in the shell, the shell language would just import `grep` as a part of the prelude and the user would have access to it as soon as they open a terminal window. *Core utils function more as libraries, not programs.*
* `PATH` would not need to exist. Rather than looking for the program in the many `PATH` dirs, the shell lang would know it exists because the util is included in the prelude.

### Application Runtime
* Applications would be sandboxed by default. Every application has access to it's own virtual filesystem that is persisted. This prevents malicious software from sharing data with privacy-sensitive software. If an application *does* need to share data with another application, well, idk yet...
* Applications will *not* implement fullscreen, windowed mode, etc. on their own, like with what happens with other display server APIs. Instead, the application will call a sort of `.fullscreen()` method and the display server will handle *all* of the implementation of the windowing mode change. This gives devs less control over the look of the window. That's probably a good thing.
