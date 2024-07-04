# NewRad

## Non-hyperboloidal wave equation test

To see if we set up the ScalarHyp_helper thorn well and the pulse just leaves the domain with no relfections.

## Low Resolution

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_H01_N16_NewRad_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_H01_N16_NewRad_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_H01_N16_NewRad.html" width="800" height="600" frameborder="0"></iframe>

```{note}
Explosion near scri doesn't happen for this run, however we get some pretty intense wave reflections. What happens when we increase resolution?
```

## Medium Resolution

n_ghost_points = 6, h_radial = 0.0075, h_cartesian = 0.007375, inner_radius = 0.295, outer_radius = 1, n_angular = 22, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.0075, output_every = 12


<video src="_static/videos/ScalarHyp_MED_NewRad_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_NewRad_LOWMED.html" width="800" height="600" frameborder="0"></iframe>

## Low Resolution, Dissipation ($\epsilon$=0.19)

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<iframe src="_static/ScalarHyp_NewRad_EPS19.html" width="800" height="600" frameborder="0"></iframe>

```{note}
Hum
```


