# pylusat changelog

## 0.5.2

2021-05-29

### Fixed

- `zonal_stats_raster` - fixed issues with the function when raster projection
  and GeoDataFrame projection are not the same by fixing the backend class
  `RasterManager`
  
### Updated

- Updated the license

## 0.5.1

2021-05-28

### Improved

- Change test framework to `pytest` to work with GitHub Actions for continuous
  integration (CI).

### Updated

- Change `RasterManager` and `distance.to_cell` from using `gdal` methods to
  `rasterio` methods.

## 0.5.0

2021-05-24

### Added

- test for `zonal_stats_raster`
- `RasterManager` - This class is similar to the `GeoDataFrameManager` in
  `pylusat.base`. It manages the basic properties and methods of a raster
  dataset, such as `wkt`, `srs`, `reproject()`, `to_array()`.
  
### Removed

- `utils.read_raster` - This function is replaced by the method in
  `RasterManager`.

### Improved

- `zonal_stats_raster` - This function now will compare the spatial reference
  system of the `zone_gdf` and the `raster`. If they are not the same, the
  function will attempt to `Warp` (reproject) the raster to match the spatial
  reference of `zone_gdf`. 

## 0.4.0

2021-04-26

### Added

- `utils.gridify` - This new function creates a grid based on the input
  GeoDataFrame.

## 0.3.4

2021-04-24

### Updated

- `distance.to_cell` - return null when no value specified presented in the
  target raster

## 0.3.3

2021-03-29

### Fixed

- `density.of_line` - fix a bug in buffering reporting "invalid GeoDataFrame"

## 0.3.2

2021-03-28

### Fixed

- `geotools.spatial_join` - fix a bug in retrieving columns of `target_gdf`

## 0.3.1

2021-03-28

### Updated

- `density.of_line` - when buffering around polygon `input_gdf` with a distance
  equal to the search radius, instead of using the original shapes, the tool
  now uses the centroids of the original polygons. This is in line with the
  ArcGIS `line density` function.
  
### Improved

- `geotools.spatial_join` - able to handle _spatial join_ of two layers with
  same column names by relying on the indices of the columns of `target_gdf`
  rather than their names

## 0.3.0

2021-02-07

### Added

- `utils.ahp` - Function added to perform AHP based on pre-defined reciprocal
  matrix.
  
### Updated

- `utils.random_ahp` - The previous `random_ahp_weight` is changed to
  `random_ahp` now. 

## 0.2.7

2021-02-01

### Improved

- `reclassify` - Loosened the requirement of ascending old value intervals. 
  Allow identical entries in new values. 

## 0.2.6

2021-01-26

### Improved

- `zonal_stats_raster` - Added `drop=True` to `reset_index`, so no pre-defined
  index name was used for the joined output of zone_gdf and zonal_stats output. 
  This will solve the problem caused by iterating zonal_stats multiple times. 

## 0.2.5

2021-01-25

### Updated

- `zonal stats` - the tool now allows users to specify a string as the prefix
  for the column name(s) of the generated statistics.

## 0.2.4

2021-01-18

### Fixed

- `select by location` - the tool now only output features met the specified
  spatial relationship.