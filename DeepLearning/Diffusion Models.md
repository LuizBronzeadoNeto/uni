### Ruído
Adição de ruído à n Imagens
Imagem + $\epsilon$
$$x_1 \leftarrow x_0\sqrt{1-\beta_1} + \epsilon \sqrt \beta_1$$
$$x_t \leftarrow x_{t-1}\sqrt{1-B_1} + \epsilon \sqrt B_1$$
onde $\epsilon \in N(0,I)$
### Treinamento
O treinamento é autosupervisionado e conduzido por correção de erro. Como as pertubações na imagem são geradas pelo modelo, ele conhece o erro real.
Onde a função de perda é definida da seguinte forma:$$L = E[|\epsilon - \epsilon_\theta(x_tt)|^2]$$
- **Hyper Suprime-Cam Subaru Strategic Program (HSC-SSP):** For Track 1, we require extremely deep optical imagery that older surveys like SDSS cannot provide. HSC provides deep, multi-band images required for calculating color and age gradients.
    
- **Galaxy Zoo & Zenodo Catalogs:** To train the U-Net for Track 1, we will utilize existing crowdsourced coordinates of known tidal interactions to generate the ground-truth binary masks.
    
- **The IllustrisTNG Project (TNG50/TNG100):** For Track 2, we will pull purely mathematical, simulated subhalos of merging galaxies to act as the noiseless ground-truth targets for the diffusion model.
