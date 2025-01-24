# EMIM 2025 Poster DATA-038
Here you can find additional information and animations of the poster [Cell Flow PET Simulations as Ground Truth for Development of PET-based Cell Tracking](https://github.com/N-Marquardt/IEEE_MIC_2024_Poster_M-03-052/blob/029e24b6513efa23ff1a85db722d5c9fde3dbebb/IEEE%20MIC%202024%20Poster%20M-03-052.pdf) presented at the EMIM 2025. 
## CeFloPS 
A preprint describing the setup and simulation steps in detail for our cell flow PET simulation model (CeFloPS) is available [here](https://arxiv.org/abs/2407.07709#). As illustrated in the poster, a simulation of 10 cells was carried out over a 600s period with 10ms time-steps, initiated with an injection at the left arm vein. As kinetic parameters for (immune) cells are lacking, the parameters for FDG as described by [Li et al. (2022)](https://jnm.snmjournals.org/content/63/8/1266.abstract) have been applied to simulate the distribution of cells in organs. Consequently, the behaviour of the simulated cells deviates from that of real cells and is closer to that of FDG molecules. 
An animated video of this simulation can be watched and downloaded [here](https://uni-muenster.sciebo.de/s/ldTQmrBX9T76Y94). A version with 100 simulated cells is also [available](https://uni-muenster.sciebo.de/s/ZH5ddElPzBZlsho). In order to validate the cell tracking algorithm, the time period between 109s and 120s was considered. The movement of the cells in this time period can be observed in the animation below or [here](https://uni-muenster.sciebo.de/s/HcmEbRPz5bua8P3). Cells depicted in red are located in blood vessels or inside the compartment *C<sub>A</sub>* of an organ and moving between two frames. Yellow cells are located in the compartment *C<sub>1</sub>* of an organ and are temporarily trapped there, meaning they do not move between two frames but can go back to compartment *C<sub>A</sub>* at a later timepoint. Green cells are located in compartment *C<sub>2</sub>* of an organ and do not move for the rest of the simulation.

<img src="10cells_from_109-120s.gif" alt="10cells_from_109-120s" width="400" />

## PET simulation

The simulated cell paths serve as input for moving sources in GATE. Each cell is simulated as a sphere of 1µm diameter with 10kBq of activity. To create PET data, the total-body scanner [Siemens Biograph Vision Quadra](https://jnm.snmjournals.org/content/63/3/476.abstract) (Siemens Healthineers) is implemented as well as the [XCAT phantom](https://aapm.onlinelibrary.wiley.com/doi/full/10.1118/1.3480985) for attenuation and scatter effects. The background created by the radioactive Lu-176 in the LSO crystals of the scanner can also be simulated. For the reconstruction algorithms, the resulting root files of the GATE simulation are transformed into listmode files. The placement files of the cells for the GATE simulation, the root files and the listmode files for simulations of 10 cells without background, as well as simulations with background and with 100 cells can be found [here](https://uni-muenster.sciebo.de/s/XErqaLyqTgPbO7I).

## Reconstructions

The generated listmode data is subsampled to only account for 20%, 5% and 1% of the simulated coincidences, thus mimicking less activity per cell. The subsampled data is then reconstructed using a classical framewise expectation maximization method (fw EM) and a new algorithm based on optimal transport (dyn opt) as described by [Schmitzer et al. (2019)](https://ieeexplore.ieee.org/abstract/document/8902066/) and [Mauritz et al. (2024)](https://epubs.siam.org/doi/full/10.1137/23M161923X). The time window from 109s to 120s was divided into 23 frames. In the animations below you can see the reconstruction results for fw EM and dyn opt site-by-site for each percentage of coincidences used, respectively. On the top of the animations the data is projected to the xy-plane, in the bottom to the xz-plane. The red stars depict the ground truth positions of the cells. 

<img src="recons_for_20percent.gif" alt="recons_for_20percent" width="400" />
<img src="recons_for_5percent.gif" alt="recons_for_5percent" width="400" />
<img src="recons_for_1percent.gif" alt="recons_for_1percent" width="400" />

To quantitavely validate and compare the reconstruction results of fw EM and dyn opt, their differences to the ground truth is calculated using the method described by [Chizat et al. (2018)](https://link.springer.com/article/10.1007/s10208-016-9331-y). For this means, a maximum distance must be defined how far a cell can be transported during a time frame. The positional errors are calculated for three different maximum transport differences of 2, 5 and 10 pixel diameters (1 pixel diameter = 5.8mm). 

<img src="comparison_recons_numberofevents.gif" alt="recons_for_1percent" width="800" />

| % of coincidences used | maximum transport in px diameter | Error fw EM in mm | Error dyn opt in mm |
| --- | --- | --- | --- |
| 20 | 2 | 7.9 | 6.6 |
| 20 | 5 | 18.7 | 15.5 |
| 20 | 10 | 35.3 | 30.4 |
| 5 | 2 | 8.7 | 8.0 |
| 5 | 5 | 20.2 | 17.1 |
| 5 | 10 | 38.0 | 32.0 |
| 1 | 2 | 10.3 | 9.0 |
| 1 | 5 | 24.8 | 18.7 |
| 1 | 10 | 46.7 | 33.6 |

## Contact

You can contact the authors under:

[European Institute for Molecular Imaging](https://www.uni-muenster.de/EIMI/), University of Münster, Röntgenstraße 16, 48149 Münster, Germany

Nils Marquardt, n.marquardt@uni-muenster.de

Tobias Hengsbach, thengsba@uni-muenster.de

Klaus P. Schäfers, schafkl@uni-muenster.de

[Institute for Computational and Applied Mathematics](https://www.uni-muenster.de/AMM/en/), University of Münster, Orléans-Ring 10, 48149 Münster, Germany

Marco Mauritz, marco.mauritz@uni-muenster.de

Benedikt Wirth, benedikt.wirth@uni-muenster.de


