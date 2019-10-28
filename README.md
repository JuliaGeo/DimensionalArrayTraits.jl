# DimensionalArrayTraits.jl
Abstract base package for dimensional arrays and their specific traits
__Note this is page currently at the discussion stage.__

## Requirements on spatial data/domain types from the user's perspective

*    Return coordinates lon/lat/depth/time (and arbitrary dimension) for a given index i,j,k,...
*    Tell what each coordinate represent (is the 3rd dimension time or depth or something else?).
*    Maybe re-use the CF convention names (longitude, latitude, time, …)
*    Subsetting based on lon/lat/depth/time (and arbitrary dimension) bounding box (how to handle irregular grid?)
*    Find the k nearest points for a given location
*    Integral over a raster (knowing the “volume” of each grid cell)
*    Time: is the value for the start, middle or (probably never) the end of the duration. Is it an average of the whole period or a specific point in the cell. These specifications should also generalise to any other dimension type.
*    Categorical dimensions with no size or regularity
*    Arrays can be plotted correctly using the grid information
*    Use cf conventions where applicable
*    For me units and other metadata can be out-of-scope, at least for now)

## Implementation/Performance 

* Zero cost indexing (only works on regular grids?)
* Lazy affine transformations on the data

## Minimal interface to be implemented for different array types of spatial data
