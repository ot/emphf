emphf
=====

This repository contains the code used for the experiments in the
paper "Cache-Oblivious Peeling of Random Hypergraphs" by Djamal
Belazzougui, Paolo Boldi, Giuseppe Ottaviano, Rossano Venturini, and
Sebastiano Vigna.

All the algorithms implemented here construct a minimal perfect hash
function for a given key set using a standard scheme based on MWHC,
that is based on finding a peeling order of a random 3-hypergraph.

* `compute_mphf_seq` computes the peeling order using the standard
  in-memory linear-time peeling algorithm, implemented with the
  xor-trick described in the paper.

* `compute_mphf_scan` computes the peeling order using the new
  algorithm proposed in the paper, but on heap-allocated memory.

* `compute_mphf_scan_mmap` computes the peeling order using the new
  algorithm proposed in the paper, using an mmapped temporary file for
  its data structure, thus in an external-memory setting.

* `compute_mphf_hem` uses a technique described in F. C. Botelho,
  R. Pagh, and N. Ziviani, “Practical perfect hashing in nearly
  optimal space”, that splits the key sets in bucket that are small
  enough that the perfect hash function is easy to compute in memory
  for each bucket.

The script `test_all.py` executes all the algorithms on a given file
(or the standard UNIX dictionary if none is provided) and checks that
the generated hash function is indeed minimal and perfect.

The project uses CMake. To build it on Unix systems it should be
sufficient to do the following:

    $ cmake .
    $ make





