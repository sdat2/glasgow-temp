# glasgow-temp

Get maximum projected temperatures for Glasgow for 2080-2100.

## Method A - CDS API request

Download each individual model as a zip file
from https://cds.climate.copernicus.eu/cdsapp#!/dataset/projections-cmip6?tab=form

```python
import cdsapi

c = cdsapi.Client()

c.retrieve(
    'projections-cmip6',
    {
        'format': 'zip',
        'temporal_resolution': 'daily',
        'experiment': 'ssp5_8_5',
        'variable': 'daily_maximum_near_surface_air_temperature',
        'level': 'single_levels',
        'date': '2080-07-30/2100-08-11',
        'area': [
            56, -5, 55,
            -4,
        ],
        'model': 'access_cm2',
    },
    'download.zip')
```

## Method B - Pangeo

Could also use `intake-esm`, and directly process netcdfs from the Pangeo catologue (problems with grids).

## Method C - Climetlab

Climetlab should hopefully enable us to use method B with more of the problems worked out.

https://github.com/ecmwf/climetlab
