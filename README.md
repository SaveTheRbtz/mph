# mph


[![Go Reference](https://pkg.go.dev/badge/github.com/SaveTheRbtz/mph.svg)](https://pkg.go.dev/github.com/SaveTheRbtz/mph)

mph is a Go package for that implements a [minimal perfect hash table][mph] over
strings. It uses the ["Hash, displace, and compress" algorithm][algo] and the
[circlehash hash function][circlehash].

Some quick benchmark results (Apple M1 Pro):

* `Build` constructs a minimal perfect hash table from a 350k word dictionary in
  100ms (construction time is linear in the size of the input).
* `Lookup`s on that dictionary take about 30ns and are 50% faster than a
  `map[string]uint32`:

```
name      time/op
Build     51.4ms ±12%
Table     13.7ns ± 0%
TableMap  42.1ns ± 1%
```

[mph]: https://en.wikipedia.org/wiki/Perfect_hash_function#Minimal_perfect_hash_function
[algo]: https://cmph.sourceforge.net/papers/esa09.pdf
[circlehash]: https://github.com/fxamacker/circlehash
