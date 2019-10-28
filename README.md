# DimensionalArrayTraits.jl
Abstract base package for dimensional arrays and their specific traits
__Note this is package currently in the discussion stage.__

## Requirements on spatial data/domain types from the user's perspective

It is proposed to add behind each point, a possible interface (from the user point of view)

*    Return coordinates lon/lat/depth/time (and arbitrary dimension) for a given index i,j,k,...

```julia
coord(A,:latitude,i,j,k) # or better coord(A,Lat(),i,j,k)  
lat(A,i,j,k) # for common dimension names
lat(A,j) # if grids are aligned with longitude/latitude/depth/time...; otherwise an error
lon
```

* Return the value at a given index i,j,k... (the result is no longer georeferenced).

```
value(A,i,j,k)
```

*    Tell what each coordinate represent (is the 3rd dimension time or depth or something else?).

```julia
coordnames(x) # would return :longitude, :latitude, ... or Lon(), Lat()
```
Use the CF convention names (longitude, latitude, time, …)

*    Subsetting based on lon/lat/depth/time (and arbitrary dimension) bounding box (how to handle irregular grid?)

```
A[Lat(x), Lon(y), Time(At(t))]
```

*    Find the k nearest points for a given location
*    Integral over a raster (knowing the "volume" of each grid cell)

```julia
volume(A,i,j,k)
```

*    Time: is the value for the start, middle or (probably never) the end of the duration. Is it an average of the whole period or a specific point in the cell. These specifications should also generalise to any other dimension type.
*    Categorical dimensions with no size or regularity
*    Arrays can be plotted correctly using the grid information

```julia
plot(A[:,:,n])
```


### Out-of-scope (at least initially) 
*    units and other metadata

## Implementation/Performance 

* Zero cost indexing (only works on regular grids?)
* Lazy affine transformations on the data

## Minimal interface to be implemented for different array types of spatial data

https://gist.github.com/meggart/e29e6381d9400ff789eefbccc109d6f9



