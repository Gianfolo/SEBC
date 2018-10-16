Slowest Teragen run
```
Number of mappers: 1
Number of reducers: 14
Mapper memory:  1280
Reducer memory:  1280

real    4m50.268s
user    0m7.054s
sys     0m0.443s
```

Fastest Teragen run
```
Number of mappers: 14
Number of reducers: 1
Mapper memory:  1280
Reducer memory:  1280

real    2m16.379s
user    0m7.231s
sys     0m0.427s
```
As you can see from the above results, the performances of the TeraGen tool are strictly related to the number of mapper: the higher the mappers (according to the number of available cores), the higher the performances.
Instead the number of reducers seems to be not really relevant for this test, and in fact we know that TeraGen don't use reduce tasks.

Slowest Terasort run
```
Number of mappers: 1
Number of reducers: 1
Mapper memory:  1280
Reducer memory:  1280

real    8m22.075s
user    0m10.926s
sys     0m0.661s
```

Fastest Terasort run
```
Number of mappers: 14
Number of reducers: 14
Mapper memory:  1280
Reducer memory:  1280

real    3m53.868s
user    0m9.037s
sys     0m0.501s
```
The TeraSort tool performances are slightly different: we can see that the results are dependent from both number of mappers and reducers because this tool use both mappers and reduce to make the computation.
