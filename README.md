# CMIP6-testbed-ML-sub-sampling-experiments

!! Documentation in progress !!

Description on how to access the 45-member CMIP6-testbed (Heimdal et al., 2025; https://iopscience.iop.org/article/10.1088/3049-4753/adddc3) and machine learning reconstructions of surface ocean pCO2 based on sub-sampling experiments of the testbed.

The CMIP6-testbed consists of 45 pickle files containing the target (surface ocean pCO2) and all driver variables (e.g. SST, SSS) for each individual testbed member; there is one individual pickle file for each of the 45 members of the testbed.

The CMIP6-testbed is publicly accessible on the Open Storage Network (OSN) pod. The path to the main folders: 

For 1982-2022: https://nyu1.osn.mghpcc.org/leap-pangeo-manual/pco2_all_members_1982-2022/post01_xgb_inputs.

For 1982-2023: https://nyu1.osn.mghpcc.org/leap-pangeo-manual/pco2_all_members_1982-2022/post01_xgb_inputs.

We also provide paths to four CMIP6-testbed surface ocean pCO2 reconstruction sub-sampling experiments: experiments LR-2yr_masked, LR-2yr_unmasked, LR-41yr and LR-41yr-collapsed. Each of these experiments include 45 Zarr files. 

LR-2yr_masked: https://nyu1.osn.mghpcc.org/leap-pubs/hatlenheimdalthea/pco2_residual_testbed_2020-2021/post02_xgb_2020-2022/reconstructions

LR-2yr_unmasked: https://nyu1.osn.mghpcc.org/leap-pubs/hatlenheimdalthea/pco2_residual_testbed_2020-2021_unmasked/post02_xgb_2020-2022/reconstructions

LR-41yr: https://nyu1.osn.mghpcc.org/leap-pubs/abbysh/pco2_gridsearch_1982-2022/post02_xgb_1982-2022_nmse_outputs/reconstructions

LR-41yr-collapsed: https://nyu1.osn.mghpcc.org/leap-pubs/hatlenheimdalthea/pco2_residual_testbed_2020-2021_collapsed/post02_xgb_2020-2022/reconstructions

The testbed is structured as follows: within the folder paths described above, there are 9 sub-folders, one for each of the Earth System Models (ESM) in the testbed (see overview below; see also Heimdal et al., 2025). Within each of the 9 folders, there are sub-folders representing each member per ESM. Note that the number of members vary between each ESM. Within each member folder, there is one pickle file (for the testbed) or one zarr file (for the reconstructions). There is a total of 45 individual pickle or zarr files (one per member) for each path provided above.

Overview of the testbed structure: 

ACCESS-ESM1-5: member_r4i1p1f1, member_r5i1p1f1

CESM2: member_r10i1p1f1, member_r11i1p1f1, member_r4i1p1f1

CESM2-WACCM: member_r1i1p1f1, member_r2i1p1f1, member_r3i1p1f1

CMCC-ESM2: member_r1i1p1f1

CanESM5: member_r10i1p2f1, member_r1i1p1f1, member_r1i1p2f1, member_r2i1p1f1, member_r2i1p2f1, member_r3i1p1f1, member_r3i1p2f1, member_r4i1p1f1, member_r4i1p2f1, member_r5i1p1f1, member_r5i1p2f1, member_r6i1p1f1, member_r6i1p2f1, member_r7i1p1f1, member_r7i1p2f1, member_r8i1p1f1, member_r8i1p2f1, member_r9i1p2f1

GFDL-ESM4: member_r1i1p1f1

MPI-ESM1-2-LR: member_r11i1p1f1, member_r12i1p1f1, member_r14i1p1f1, member_r15i1p1f1, member_r16i1p1f1, member_r22i1p1f1, member_r23i1p1f1, member_r26i1p1f1, member_r27i1p1f1

UKESM1-0-LL: member_r1i1p1f2, member_r2i1p1f2, member_r3i1p1f2, member_r4i1p1f2, member_r8i1p1f2

Here is an example of how to open the CMIP6-testbed pickle file for ACCESS member r5i1p1f1 from the OSN pod:

testbed = pd.read_pickle('https://nyu1.osn.mghpcc.org/leap-pangeo-manual/pco2_all_members_1982-2022/post01_xgb_inputs/ACCESS-ESM1-5/member_r5i1p1f1/MLinput_ACCESS-ESM1-5_r5i1p1f1_mon_1x1_198202_202212.pkl')

Here is an example of how to open the reconstruction Zarr file for ACCESS member r4i1p1f1 for experiment LR-41yr-collapsed from the OSN pod:

Reconstruction = xr.open_dataset('https://nyu1.osn.mghpcc.org/leap-pubs/hatlenheimdalthea/pco2_residual_testbed_2020-2021_collapsed/post02_xgb_2020-2022/reconstructions/ACCESS-ESM1-5/member_r4i1p1f1/recon_pCO2_ACCESS-ESM1-5_member_r4i1p1f1_mon_1x1_202002_202201.zarr', engine='zarr')

To access any of the other members, swap out the member and ESM names using the list provided above. 

