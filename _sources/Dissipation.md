# Dissipation 

TEM2 on our lopsided derivative, dissipation of order 3, on $r$,$\theta$,$\phi$.

## h=0.01, n=10, eps = 0.19

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 10, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_LOW_TEM2_N10_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_LOW_TEM2_N10_EPS19_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_LOW_TEM2_N10_EPS19.html" width="800" height="600" frameborder="0"></iframe>


## h=0.01, n=35, eps = 0.19

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 35, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_LOW_TEM2_N35_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_LOW_TEM2_N35_EPS19_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_LOW_TEM2_N10&35_EPS19.html" width="800" height="600" frameborder="0"></iframe>


## h=0.02, dt=0.02, n=32, eps = 0.19

n_ghost_points = 6, h_radial = 0.02, h_cartesian = 0.02, inner_radius = 0.3, outer_radius = 1, n_angular = 32, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.02, output_every = 9

<video src="_static/videos/ScalarHyp_TEM2_H02_N32_T02_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H02_N32_T02_EPS19_sliced.mp4"  controls width="700" height="520" ></video>


## h=0.03, dt = 0.01, n=16, eps = 0.19

n_ghost_points = 6, h_radial = 0.03, h_cartesian = 0.03, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_TEM2_H03_N16_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H03_N16_EPS19_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_TEM2_H03_N16_EPS19.html" width="800" height="600" frameborder="0"></iframe>


```{note}
I forgot about the CFL condition, i should have increased the time step as well, next simulation
```

## h=0.03, dt=0.03, n=16, eps = 0.19

n_ghost_points = 6, h_radial = 0.03, h_cartesian = 0.03, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.03, output_every = 9

<video src="_static/videos/ScalarHyp_TEM2_H03_N16_T03_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H03_N16_T03_EPS19_sliced.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/ScalarHyp_TEM2_H03_N16_T03_EPS19.html" width="800" height="600" frameborder="0"></iframe>

```{note}
The growth near scri didn't appear on this run but the waveform became very different, much wider and spreading across $r$. Can't go this low on resolution i guess.
```

## h=0.03, dt=0.03, n=32, eps = 0.19

n_ghost_points = 6, h_radial = 0.03, h_cartesian = 0.03, inner_radius = 0.3, outer_radius = 1, n_angular = 32, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.03, output_every = 9

<video src="_static/videos/ScalarHyp_TEM2_H03_N32_T03_EPS19_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H03_N32_T03_EPS19_sliced.mp4"  controls width="700" height="520" ></video>


```{note}
I can't retrieve the 1D data, the hdf5 data came in a weird format, changed the labelling of patches and my code no longer works. Could adapt it to this weird bug but it's a bit annoying, i think the 2d data is enough to say the waveform is still spreading too much.
```

I will run the same simulation for t=24 instead of 12 to see if it explodes at later times. I will output every 50 so it will be less detailed but i just care about what happens at later times.

n_ghost_points = 6, h_radial = 0.03, h_cartesian = 0.03, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.03, output_every = 50

<video src="_static/videos/ScalarHyp_TEM2_H03_N32_T03_EPS19_LONG_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H03_N32_T03_EPS19_LONG_sliced.mp4"  controls width="700" height="520" ></video>

Okay so we definitely can see the growth near scri appearing, although it is still very small a the end of this simulation. This reveals that our scheme is unstable, since an increase in resolution leads to a faster abnormal field growth.

## h=0.01, dt=0.01, n=16, eps = 0.19, dissipation only in $r$ direction

n_ghost_points = 6, h_radial = 0.01, h_cartesian = 0.01, inner_radius = 0.3, outer_radius = 1, n_angular = 16, outer_boundary_size = 6 , patch_boundary_size = 6, additional_overlap_size = 2, time_step = 0.01, output_every = 9

<video src="_static/videos/ScalarHyp_TEM2_H01_N16_EPS19_DISSINR_scri.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/ScalarHyp_TEM2_H01_N16_EPS19_DISSINR_sliced.mp4"  controls width="700" height="520" ></video>
