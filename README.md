# Do

Do is a subset of [Mk](https://9fans.github.io/plan9port/man/man1/mk.html).

# Wait...What ?

You may be thinking, "why the hell do you people want to do a YAM (Yet Another Make) ?"
and I don't blame you. Well, besides the obvious reasons (fun and no profit) we are
so happy that [mk](https://9fans.github.io/plan9port/man/man1/mk.html) is simpler
than make that we want something even simpler.

Well, isn't mk pretty minimal ? Actually it is, if you compare with GNU's Make you
will possibly cry, and our idea is not to substitute make or mk (mk substitutes make
actually =)), like I said on the beggining of the docs, Do is a **subset** of mk.

The idea of Do was born from multiple Makefiles and mkfiles that had virtual (for mk) and
.PHONY (for Make). Almost all targets where like that. Then we realized that for a lot
of languages having a tool that is specialized is generating (making) files is
almost useless, we where using the dependency mechanism that comes with these
tools (which is great) but was using none of the file making mechanisms.

An example of complex feature that exists only to make compiling code (or stuff similar)
easier is the aggregate features from [mk](https://9fans.github.io/plan9port/man/man1/mk.html),
the only tool supported to work on aggregates are [ar](https://9fans.github.io/plan9port/man/man1/9c.html):

```
Names of the form a(b) refer to member b of the aggregate a.
Currently, the only aggregates supported are 9ar (see 9c(1)) archives.
```

The feature may be useful for other stuff than compiling C code and generating archive
files, but we failed to find usecases for these outside C code compiling and started
to like the idea of having a even simpler tool to automate chains of commands (do's)
that don't necessarily make a file directly.

The idea is to start just with a really small set of features:

* targets
* pre-requisites
* concurrent execution
* multiple shell support

And that is it, no code to handle file generation, aggregated files, etc.
There is absolutely nothing wrong with mk and we are going to keep using
it to compile C code, or when its file generation features make sense.
