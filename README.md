# IEEE MIC 2024 Poster M-03-052
Here you can find additional information and animations of the poster [Cell Flow PET Simulations for Validation of Cell Tracking Algorithms](https://github.com/N-Marquardt/IEEE_MIC_2024_Poster_M-03-052/blob/029e24b6513efa23ff1a85db722d5c9fde3dbebb/IEEE%20MIC%202024%20Poster%20M-03-052.pdf) presented at the 2024 IEEE NSS MIC RTSD. 
## CeFloPS 
A preprint describing the setup and simulation steps in detail for our cell flow PET simulation model (CeFloPS) is available [here](https://arxiv.org/abs/2407.07709#). As illustrated in the poster, a simulation of 10 cells was carried out over a 600s period with 10ms time-steps, initiated with an injection at the left arm vein. As kinetic parameters for (immune) cells are lacking, the parameters for FDG as described by [Li et al. (2022)](https://jnm.snmjournals.org/content/63/8/1266.abstract) have been applied to simulate the distribution of cells in organs. Consequently, the behaviour of the simulated cells deviates from that of real cells and is closer to that of FDG molecules. 
An animated video of this simulation can be watched and downloaded [here](https://uni-muenster.sciebo.de/s/ldTQmrBX9T76Y94). A version with 100 simulated cells is also [available](https://uni-muenster.sciebo.de/s/ZH5ddElPzBZlsho). In order to validate the cell tracking algorithm, the time period between 109 seconds and 120 seconds was considered. The movement of the cells in this time period can be observed in the animation below or [here](https://uni-muenster.sciebo.de/s/HcmEbRPz5bua8P3).

<img src="10cells_from_109-120s.gif" alt="10cells_from_109-120s" width="400" />

## PET simulation

The simulated cell paths serve as input for moving sources in GATE. Each cell is simulated as a sphere of 1µm diameter with 10kBq of activity. To create PET data, the total-body scanner [Siemens Biograph Vision Quadra](https://jnm.snmjournals.org/content/63/3/476.abstract) (Siemens Healthineers) is implemented as well as the [XCAT phantom](https://aapm.onlinelibrary.wiley.com/doi/full/10.1118/1.3480985) for attenuation and scatter effects. The background created by the radioactive Lu-176 in the LSO crystals of the scanner can also be simulated. For the reconstruction algorithms, the resulting root files of the GATE simulation are transformed into listmode files. The placement files of the cells for the GATE simulation, the root files and the listmode files for simulations of 10 cells and 100 cells with and without background can be found [here](https://uni-muenster.sciebo.de/s/XErqaLyqTgPbO7I).

## Reconstructions

 

<img src="recons_for_20percent.gif" alt="recons_for_20percent" width="400" />
<img src="recons_for_5percent.gif" alt="recons_for_5percent" width="400" />
<img src="recons_for_1percent.gif" alt="recons_for_1percent" width="400" />
<img src="comparison_recons_numberofevents.gif" alt="recons_for_1percent" width="800" />

