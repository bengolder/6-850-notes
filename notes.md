
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [
            ['$','$'],
            ['\\(','\\)']
        ]
    }
});
</script>

-----------------------------------------------------------------------------

## Triangulation

### Triangulation: Definition

* Triangulation of a simple polygon $P$: decomposition of $P$ into triangles
  by a maximal set of non-intersecting diagonals.
* Diagonal: an open line segment that connects two vertices of $P$ and lies in
  the interior of $P$.
* Triangulations are usually not unique.

### Motivation: Guarding an Art Gallery

* an art gallery has several rooms.
* Each room is guarded by cameras that see in all directions.
* Want to have few cameras that cover the whole gallery.

### Triangulation: Existence

* Theorem:

    * Every simple polygon admits a triangulation.
    * any triangulation of a simple polygon with $n$ vertices consists of
      exactly $n - 2$ triangles.

* Proof:
    
    * Base case: $n = 3$

        * 1 triangle: ($= n - 2$)
        * trivially correct

    * Inductive step: assume theorem holds for all $m < n$


### Inductive Step

* First, prove existence of a diagonal:

    * let $v$ be the leftmost vertex of $P$.
    * let $u$ and $w$ be the two neighboring vertices of $v$.
    * if open segment $uw$ lies inside $P$, then $uw$ is a diagonal.

* If open segment $uw$ does not lie inside $P$.

    * there are one or more vertices inside triangle $uvw$
    * of those vertices, let $v'$ be the __farthest one__ from $uw$
    * segment $vv'$ cannot intersect any edge of $P$, so $vv'$ is a diagonal.

* Thus a diagonal exists
* Can recurse on both sides
* Math works out: $(n\_1 - 2) + (n\_2 - 2) = (n\_1 + n\_2 - 2) - 2$

### Digression

* Could we have picked the __leftmost__ vertex inside the triangle $uvw$?
* No:

    * $p$ works
    * $q$ does not.

### Back to cameras (relevant to fan triangulations)

* Where should we put the cameras?
* idea: cover every triangle

    * each triangle is assigned nodes of type $A B C$ (one type for each
      vertex).
    * Can choose the least frequent color class --> $\frac{n}{3}$ cameras
      max.

### How to triangulate fast

* partition the polygon into y-monotone parts, i.e., into polygons $P$ such
* that an intersection of any horizontal line $L$ with $P$ is one
  uninterrupted segment.
* Triangulate the monotone parts.

### Monotone partitioning

* Line sweep (top down)
* Vertices where the direction changes downward to upward are called turn
  vertices.To have $y$-monotone pieces, we need to get rid of turn vertices:

    * When we encounter a turn vertex, it might be necessary to introduce a
      diagonal and split the polygon into pieces.









