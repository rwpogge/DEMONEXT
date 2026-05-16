# DEMONEXT Winer System Parameters

Configuration data from the Winer Observatory installation.

## Telescope Focus

Nominal Focus: 32200 (V filter)

Filter focus deltas:

| Filter | deltaFoc |
|:------:|:--------:|
|   B    |    69    |
|   V    |     0    |
|   R    |  -114    |
|   I    |   -60    |
|   g    |  -110    |
|   r    |   -47    |
|   i    |   -46    |
|   z    |    60    |
| clear  |   -67    |
| empty  |     0    |


## Science Guiding Mode

```
  Threshold: 10.0    # detection threshold, sigma above sky
  MinFWHM: 1.25      # min and max "star" FWHM in pixels
  MaxFWHM: 4.0
  MaxEll: 0.3        # maximum image ellipticity (galaxy, CRE rejection)
  MinPeak: 5000.0    # minimum peak pixel above sky in ADU
  MaxPeak: 55000.0   # maximum peak pixel including sky in ADU (saturation avoidance)
  OffsetTol: 5       # catalog matcher offset tolerance in pixels
  CalXStep: 10       # science guider calibration offset in X (seconds)
  CalYStep: 10       # science guider calibration offset in Y (seconds)
  MinStars: 5        # minimum number of stars to compute offsets
  Gain: 0.8          # guide correction gain factor (dimensionless)
  CCDRotAng: 90.0    # Nominal CCD-to-sky rotation angle in degrees CW
  Guide_A: 0.0       # guider calibration N-S scale in units of sec/pixel
  Guide_B: 0.0       # guider calibration E-W scale in units of sec/pixel
  Guide_Theta: -90.0 # guider rotation (usually -CCDRotAng)
```

