gopoker
=====

Uses same algorithm and techniques as Deuces: 
https://github.com/worldveil/deuces

Hand evaluator command line utility for Go for 5, 6, and 7 card hands. Hands are given a rank in the range `[1, 7462]`, where 1 is a Royal Flush.
Command line options were added to read a list of hands from a text file, and to optionally print the evaluated hand after the computed rank.

```
  evaluate <hand>
  evaluate [-f <input_filename>] [-h]
```

Examples to evaluate a single hand:
```
  $ evaluate As Ks Qs Js Ts 7h
  1
  $ evaluate 7h 5d 4c 3s 2h
  7462
  $ evaluate Ts 9d 8c 7c 6h As
  1604
```

Examples to evaluate a list of hands from a file:
```
  $ evaluate -f all-five-card-hands.txt -h > all-five-card-hands.result.txt
  $ head all-five-card-hands.result.txt
  9 2c 3c 4c 5c 6c
  1599 2c 3c 4c 5c 7c
  1598 2c 3c 4c 6c 7c
  1597 2c 3c 5c 6c 7c
  1596 2c 4c 5c 6c 7c
  8 3c 4c 5c 6c 7c
  1595 2c 3c 4c 5c 8c
  1594 2c 3c 4c 6c 8c
  1593 2c 3c 5c 6c 8c
  1592 2c 4c 5c 6c 8c
```

Example to evaluate a list from a file, with only hand values in the output:
```
  $ evaluate -f all-five-card-hands.txt | head
  9
  1599
  1598
  1597
  1596
  8
  1595
  1594
  1593
  1592
```

## Benchmark files

I forked this project to generate a file that could be used as a benchmark for the
correct hand valuations. Now I can implement hand valuators in another language and
generate the same output file and check for no diffs.

The file `all-five-card-hands.txt` contains all 2598960 possible five card hands from
a standard 52 card deck.

The file `all-five-card-hands.result.txt` contains the same 2598960 possible hands after
they have been run through the evaluate function, printing the hand value and the hand
itself. This is the benchmark file.
