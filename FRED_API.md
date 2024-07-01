# FRED API Documentation

**Base URL:** `https://api.stlouisfed.org/fred`

**Description:** The Federal Reserve Economic Data (FRED) API provides access to a wide range of economic data, including categories, releases, series, sources, and tags. This API is essential for tracking economic indicators that influence fertilizer demand, such as GDP and interest rates.

## Endpoints and Usage:

### Categories
- `fred/category` - Get a category.
- `fred/category/children` - Get the child categories for a specified parent category.
- `fred/category/related` - Get the related categories for a category.
- `fred/category/series` - Get the series in a category.
- `fred/category/tags` - Get the tags for a category.
- `fred/category/related_tags` - Get the related tags for a category.

### Releases
- `fred/releases` - Get all releases of economic data.
- `fred/releases/dates` - Get release dates for all releases of economic data.
- `fred/release` - Get a release of economic data.
- `fred/release/dates` - Get release dates for a release of economic data.
- `fred/release/series` - Get the series on a release of economic data.
- `fred/release/sources` - Get the sources for a release of economic data.
- `fred/release/tags` - Get the tags for a release.
- `fred/release/related_tags` - Get the related tags for a release.
- `fred/release/tables` - Get the release tables for a given release.

### Series
- `fred/series` - Get an economic data series.
- `fred/series/categories` - Get the categories for an economic data series.
- `fred/series/observations` - Get the observations or data values for an economic data series.
- `fred/series/release` - Get the release for an economic data series.
- `fred/series/search` - Get economic data series that match keywords.
- `fred/series/search/tags` - Get the tags for a series search.
- `fred/series/search/related_tags` - Get the related tags for a series search.
- `fred/series/tags` - Get the tags for an economic data series.
- `fred/series/updates` - Get economic data series sorted by when observations were updated on the FRED® server.
- `fred/series/vintagedates` - Get the dates in history when a series' data values were revised or new data values were released.

### Sources
- `fred/sources` - Get all sources of economic data.
- `fred/source` - Get a source of economic data.
- `fred/source/releases` - Get the releases for a source.

### Tags
- `fred/tags` - Get all tags, search for tags, or get tags by name.
- `fred/related_tags` - Get the related tags for one or more tags.
- `fred/tags/series` - Get the series matching tags.

### Maps API
The FRED® Maps API is a web service that allows developers to write programs and build applications to harvest data and shape files of series available on the maps found in the FRED website hosted by the Economic Research Division of the Federal Reserve Bank of St. Louis. Not all series that are in FRED have geographical data.

#### Endpoints
- `Shape Files`
- `Series Group Meta`
- `Series Regional Data`
- `Regional Data`

## Example Usage:
```yaml
data_sources:
  FRED:
    base_url: https://api.stlouisfed.org/fred
    description: >
      The Federal Reserve Economic Data (FRED) API offers a wealth of economic data, including critical metrics like GDP and federal funds interest rates, which are essential for understanding broader economic trends that impact fertilizer demand.
    endpoints:
      - name: GDP Data
        path: /series/observations
        params:
          api_key: YOUR_API_KEY
          file_type: json
          observation_start: '2010-01-01'
          observation_end: '2023-12-31'
          series_id: GDP
        description: >
          This endpoint retrieves GDP data from January 2010 to December 2023, providing insights into economic growth trends.
      - name: Interest Rate Data
        path: /series/observations
        params:
          api_key: YOUR_API_KEY
          file_type: json
          observation_start: '2010-01-01'
          observation_end: '2023-12-31'
          series_id: FEDFUNDS
        description: >
          This endpoint retrieves federal funds interest rate data from January 2010 to December 2023, which is useful for analyzing monetary policy impacts.
