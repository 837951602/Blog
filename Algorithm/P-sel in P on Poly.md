[Moved from](https://github.com/837951602/Misc/blob/master/Algo/P-sel%20in%20P%20on%20Poly.md)

[Reference](https://studylib.net/doc/14062863/semi-feasible-algorithms-hem-ogi-chapter-3-csc-286-486-un...)

# P-sel in P/n^2

Say `g` is the selector function, aka. 

    g(a,b)=a or g(a,b)=b
    f(a) or f(b) <=> f(g(a),g(b))

Make graph G: elements in f. If g(a,b)=b, then there's an edge from a to b.

Define superloser: a set of log(n+1), that reaches every element in 0-1 step. 

To prove superloser exist, notice that one element reaches more than half nodes. Remove them and repeat.

If f(x), then one of the superloser reaches there. Else, by def, no y:f(y) reaches there.

# P-sel in NP/n

[Extra ref](http://www.matrix67.com/blog/archives/746)

Let a be the node where most edges comes from a. If some b is not in G(a) or G(G(a)), then

    b -> a and b -> G(a)

and b is at least 1 out edge more than a. Thus b is in G(a) or G(G(a)).

Doesn't work if there's no node. An extra bit can be provided in this case.
