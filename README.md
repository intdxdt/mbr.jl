#mbr.jl
axis aligned minimum bounding box (MBR).
inspired by [JTS Envelope](https://github.com/simplegeo/jts/blob/master/src/com/vividsolutions/jts/geom/Envelope.java)

##api

Create bounding box using 4 values (min max x) & (min max y)
  
*MBR(x1::Float64, x2::Float64, y1::Float64, y2::Float64)*

Create bounding box using 2 points

*MBR(p1::Vector{Real}, p2::Vector{Real})*

*MBR(p1::(Real,Real), p2::(Real,Real))*

##example
```julia
include("../mbr.jl")
m00 = MBR(0, 0, 0, 0);
expand(m00, 2, 2);

m0 = MBR(1, 1, 1, 1);
expandby(m0, 1, 1);

m1 = MBR(0, 2, 0, 2);
m2 = MBR(4, 8, 5, 9);

println (equals(m0, m1));
println (equals(m00, m1));
println (isnull(intersection(m1, m2)));
println (distance(m1, m2)); #hypot(2,3)

#MBR(1.0,2.000045,1.0,2.00001)
println(MBR((1, 1), (2.000045, 2.00001)))

println (contains(m1, [1.5, 1.5])) #true
println (completely_contains(m1, 1.5, 1.5)) #true

#see test for more examples

```

#test

```julia test/test.jl```

#lic
MIT



