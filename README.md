# png-graph-generator
Bash script for generating a png call graph of a programm. 

Uses [gprof2dot](https://github.com/jrfonseca/gprof2dot) to convert the callgrind output to a png graph


# Usage:

```
  graph.sh your_program [program_arguements]
```

## Output

> A node in the output graph represents a function and has the following layout:

    +------------------------------+
    |        function name         |
    | total time % ( self time % ) |
    |         total calls          |
    +------------------------------+

> where:

>  * _total time %_ is the percentage of the running time spent in this function and all its children;
>  * _self time %_ is the percentage of the running time spent in this function alone;
>  * _total calls_ is the total number of times this function was called (including recursive calls).

> An edge represents the calls between two functions and has the following layout:

                total time %
                  calls
    parent --------------------> children

> Where:

>  * _total time %_ is the percentage of the running time transfered from the children to this parent (if available);
>  * _calls_ is the number of calls the parent function called the children.

For more information check original [repository](https://github.com/jrfonseca/gprof2dot)

# Requirements

  * [Python](http://www.python.org/download/): known to work with version 2.7 and 3.3; it will most likely _not_ work with earlier releases.
  * [Graphviz](http://www.graphviz.org/Download.php): tested with version 2.26.3, but should work fine with other versions.
  * [Valgrind](http://valgrind.org/)
  

## Debian/Ubuntu users

  * Run:

```
        apt-get install python graphviz valgrind
```


# Download

  * [PyPI](https://pypi.python.org/pypi/gprof2dot/)

```
        pip install gprof2dot
```

  * [Standalone script](https://raw.githubusercontent.com/jrfonseca/gprof2dot/master/gprof2dot.py)

  * [Git repository](https://github.com/jrfonseca/gprof2dot)


