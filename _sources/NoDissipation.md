# No Dissipation

## Low Resolutions, TEM comparison

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 10, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

TEM1

<video src="_static/videos/ScalarHyp_EPS0_TEM1_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_EPS0_TEM1_sliced.mp4"  controls width="700" height="520" ></video>

TEM2

<video src="_static/videos/ScalarHyp_EPS0_TEM2_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_EPS0_TEM2_sliced.mp4"  controls width="700" height="520" ></video>

TEM4

<video src="_static/videos/ScalarHyp_EPS0_TEM4_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_EPS0_TEM4_sliced.mp4"  controls width="700" height="520" ></video>

COMPARISON

<iframe src="_static/ScalarHyp_TEMS_EPS0.html" width="800" height="600" frameborder="0"></iframe>

```{note}
**Conclusion**: Higher order of accuracy TEM seems to explode a little slower, but not significantly so. :/
```


**n=35** (TEM2)

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 35, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_no_dissipation_n35_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_no_dissipation_n35_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_TEM2_EPS0_NCOMPARISON.html" width="800" height="600" frameborder="0"></iframe>

```{note}
Increasing angular resolution doesn't seem to have made any difference at all..
```

## Medium Resolution, TEM comparison

<iframe src="_static/ScalarHyp_MED_TEMS_EPS0.html" width="800" height="600" frameborder="0"></iframe>

```{note}
**Conclusion**: this growth is unstable as it became larger when the resolution increased. 
```
