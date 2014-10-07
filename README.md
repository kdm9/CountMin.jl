CountMin.jl
===========

[![Build Status](https://travis-ci.org/kdmurray91/CountMinSketch.jl.svg?branch=master)](https://travis-ci.org/kdmurray91/CountMinSketch.jl)


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
    # Each cell will be a Uint8, so can count to 255. You can use any unsigned
    # type as the cell type.
    cms = CountMinSketch{Uint8}(4, 1000)
    # add the hash value of something
    add!(cms, hash("Hello"))
    assert(contains(cms, hash("Hello")) == 1)
    add!(cms, hash("Hello"))
    add!(cms, hash("Hello"))
    add!(cms, hash("Hello"))
    assert(contains(cms, hash("Hello")) == 4)
