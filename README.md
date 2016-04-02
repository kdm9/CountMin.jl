CountMin.jl
===========

[![Build Status](https://travis-ci.org/kdmurray91/CountMin.jl.svg?branch=master)](https://travis-ci.org/kdmurray91/CountMin.jl)

A count-min-sketch implementation for Julia. See
[Wikipedia](https://en.wikipedia.org/wiki/Count%E2%80%93min_sketch) or the
[original paper](http://dimacs.rutgers.edu/~graham/pubs/papers/cm-full.pdf) for
more information on the background of this data structure.


API
---

Real documentation is on its way. In the mean time, read the tests as they have
a fairly full description of the API.

The API tries to follow the Julia standard method names.

    # make a CMS with 4 tables of ~1000 cells
    # Each cell will be a UInt8, so can count to 255. You can use any unsigned
    # integral type as the cell type.
    cms = CountMinSketch{UInt8}(4, 1000)

    # add the string "Hello"
    push!(cms, "Hello")
    assert(cms["Hello"] == 1)

    # Add 3 counts of the string "World"
    add!(cms, "World", 3)
    assert(cms["World"] == 3)

    # Remove the count of "Hello"
    pop!(cms, "Hello")
    assert(cms["Hello"] == 0)

    # Remove two counts of "World"
    add!(cms, "World", -2)
    assert(cms["World"] == 1)
