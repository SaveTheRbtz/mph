# mph


[![Go Reference](https://pkg.go.dev/badge/github.com/SaveTheRbtz/mph.svg)](https://pkg.go.dev/github.com/SaveTheRbtz/mph)

mph is a Go package for that implements a [minimal perfect hash table][mph] over
strings. It uses the ["Hash, displace, and compress" algorithm][algo]  and the
[xxh3 hash function][xxh3].

Some quick benchmark results (this is on an Intel(R) Xeon(R) CPU @ 2.80GHz):

* `Build` constructs a minimal perfect hash table from a 350k word dictionary in
  100ms (construction time is linear in the size of the input).
* `Lookup`s on that dictionary take about 30ns and are 50% faster than a
  `map[string]uint32`:

```
name      time/op
Build      101ms ± 3%
Table     28.1ns ± 2%
TableMap  63.9ns ± 3%
```

[mph]: https://en.wikipedia.org/wiki/Perfect_hash_function#Minimal_perfect_hash_function
[algo]: https://cmph.sourceforge.net/papers/esa09.pdf
[xxh3]: https://github.com/zeebo/xxh3
