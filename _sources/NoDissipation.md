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

```{admonition} Conclusion
Higher order of accuracy TEM seems to explode a little slower, but not significantly so. :/
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


```{admonition} Conclusion
this growth is unstable as it became larger when the resolution increased. 
```

## TEM2, TURN OFF ANGULAR DERIVATIVES. 

This is weird since it will most likely create some problems in the interpatch spherical boundary.

Copy this code into calc_rhs.cc:



    if (usejacobian){

      JacPDstandardNth1u2 = 0*J11L*PDstandardNth1u2 + 0*J21L*PDstandardNth2u2 + 
        J31L*PDstandardNth3u2;
      
      JacPDstandardNth1v2 = 0*J11L*PDstandardNth1v2 + 0*J21L*PDstandardNth2v2 + 
        J31L*PDstandardNth3v2;
      
      JacPDstandardNth2u2 = 0*J12L*PDstandardNth1u2 + 0*J22L*PDstandardNth2u2 + 
        J32L*PDstandardNth3u2;
      
      JacPDstandardNth2v2 = 0*J12L*PDstandardNth1v2 + 0*J22L*PDstandardNth2v2 + 
        J32L*PDstandardNth3v2;
      
      JacPDstandardNth3u2 = 0*J13L*PDstandardNth1u2 + 0*J23L*PDstandardNth2u2 + 
        J33L*PDstandardNth3u2;
      
      JacPDstandardNth3v2 = 0*J13L*PDstandardNth1v2 + 0*J23L*PDstandardNth2v2 + 
        J33L*PDstandardNth3v2;
      
      JacPDstandardNth11u2 = 0*dJ111L*PDstandardNth1u2 + 
        2*(J11L*(J21L*0*PDstandardNth12u2 + J31L*0*PDstandardNth13u2) + 
        J21L*J31L*0*PDstandardNth23u2) + dJ211L*0*PDstandardNth2u2 + 
        dJ311L*PDstandardNth3u2 + 0*PDstandardNth11u2*pow(J11L,2) + 
        0*PDstandardNth22u2*pow(J21L,2) + PDstandardNth33u2*pow(J31L,2);
      
      JacPDstandardNth22u2 = 0*dJ122L*PDstandardNth1u2 + 
        2*(J12L*(J22L*0*PDstandardNth12u2 + J32L*0*PDstandardNth13u2) + 
        J22L*J32L*0*PDstandardNth23u2) + dJ222L*0*PDstandardNth2u2 + 
        dJ322L*PDstandardNth3u2 + 0*PDstandardNth11u2*pow(J12L,2) + 
        0*PDstandardNth22u2*pow(J22L,2) + PDstandardNth33u2*pow(J32L,2);
      
      JacPDstandardNth33u2 = 0*dJ133L*PDstandardNth1u2 + 
        2*(J13L*(J23L*0*PDstandardNth12u2 + J33L*0*PDstandardNth13u2) + 
        J23L*J33L*0*PDstandardNth23u2) + dJ233L*0*PDstandardNth2u2 + 
        dJ333L*PDstandardNth3u2 + 0*PDstandardNth11u2*pow(J13L,2) + 
        0*PDstandardNth22u2*pow(J23L,2) + PDstandardNth33u2*pow(J33L,2);
    }

Copy this code into calc_rhs_boundary.cc:




    if (usejacobian){

      JacPDonesided2ndTEM21u2 = 0*J11L*PDonesided2ndTEM21u2 + 
        0*J21L*PDonesided2ndTEM22u2 + J31L*PDonesided2ndTEM23u2;
      
      JacPDonesided2ndTEM21v2 = 0*J11L*PDonesided2ndTEM21v2 + 
        0*J21L*PDonesided2ndTEM22v2 + J31L*PDonesided2ndTEM23v2;
      
      JacPDonesided2ndTEM22u2 = 0*J12L*PDonesided2ndTEM21u2 + 
        0*J22L*PDonesided2ndTEM22u2 + J32L*PDonesided2ndTEM23u2;
      
      JacPDonesided2ndTEM22v2 = 0*J12L*PDonesided2ndTEM21v2 + 
        0*J22L*PDonesided2ndTEM22v2 + J32L*PDonesided2ndTEM23v2;
      
      JacPDonesided2ndTEM23u2 = 0*J13L*PDonesided2ndTEM21u2 + 
        0*J23L*PDonesided2ndTEM22u2 + J33L*PDonesided2ndTEM23u2;
      
      JacPDonesided2ndTEM23v2 = 0*J13L*PDonesided2ndTEM21v2 + 
        0*J23L*PDonesided2ndTEM22v2 + J33L*PDonesided2ndTEM23v2;
      
      JacPDonesided2ndTEM211u2 = 0*dJ111L*PDonesided2ndTEM21u2 + 
        2*(J11L*(J21L*0*PDonesided2ndTEM212u2 + 0*J31L*PDonesided2ndTEM213u2) + 
        J21L*J31L*0*PDonesided2ndTEM223u2) + dJ211L*0*PDonesided2ndTEM22u2 + 
        dJ311L*PDonesided2ndTEM23u2 + 0*PDonesided2ndTEM211u2*pow(J11L,2) + 
        0*PDonesided2ndTEM222u2*pow(J21L,2) + PDonesided2ndTEM233u2*pow(J31L,2);
      
      JacPDonesided2ndTEM222u2 = 0*dJ122L*PDonesided2ndTEM21u2 + 
        2*(J12L*(J22L*0*PDonesided2ndTEM212u2 + 0*J32L*PDonesided2ndTEM213u2) + 
        J22L*J32L*0*PDonesided2ndTEM223u2) + dJ222L*0*PDonesided2ndTEM22u2 + 
        dJ322L*PDonesided2ndTEM23u2 + 0*PDonesided2ndTEM211u2*pow(J12L,2) + 
        0*PDonesided2ndTEM222u2*pow(J22L,2) + PDonesided2ndTEM233u2*pow(J32L,2);
      
      JacPDonesided2ndTEM233u2 = 0*dJ133L*PDonesided2ndTEM21u2 + 
        2*(J13L*(J23L*0*PDonesided2ndTEM212u2 + 0*J33L*PDonesided2ndTEM213u2) + 
        J23L*J33L*0*PDonesided2ndTEM223u2) + dJ233L*0*PDonesided2ndTEM22u2 + 
        dJ333L*PDonesided2ndTEM23u2 + 0*PDonesided2ndTEM211u2*pow(J13L,2) + 
        0*PDonesided2ndTEM222u2*pow(J23L,2) + PDonesided2ndTEM233u2*pow(J33L,2);
    }

<video src="_static/videos/NO_ANG_DER_sliced.mp4"  controls width="700" height="520" ></video>

<video src="_static/videos/NO_ANG_DER_scri.mp4"  controls width="700" height="520" ></video>

<iframe src="_static/NO_ANG_DER.html" width="800" height="600" frameborder="0"></iframe>


```{admonition} Conclusion
I guess turning off he angular derivatives (only on the multipatches) doesn't prevent the growth. But did i actually turn the angular derivatives off? 
```

*Non-spherical initial data*

<video src="_static/videos/NO_ANG_DER_NON_SPH_sliced.mp4"  controls width="700" height="520" ></video>

> I guess i did turn the angular derivatives off in the multipatch region.

