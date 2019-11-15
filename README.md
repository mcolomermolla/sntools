# sntools
Event generator for simulating supernova neutrino bursts in Hyper-Kamiokande (or other water Cherenkov detectors).


### Input
Text file(s) containing information about neutrino fluxes produced by the supernova.
sntools distinguishes between three flavours: nu_e, anti-nu_e and nu_x (where nu_x stands for nu_mu or nu_tau or their respective antineutrinos).
The following input formats are supported; see the source files in the `formats/` directory for details.

#### Nakazato format
Used by recent simulations by the Nakazato group. Fluxes for 13 and 20 solar mass progenitors are included as `fluxes/intp1301.data` and `fluxes/intp2001.data`. [A description of the format and fluxes for more progenitors are available online.](http://asphwww.ph.noda.tus.ac.jp/snn/index.html)
If you use these included models in your work, please cite [Nakazato et al., ApJ Supp. 205 (2013) 2](https://arxiv.org/abs/1210.6841).

#### Gamma format
Text file containing time, mean energy, mean squared energy and luminosity. These parameters describe a Gamma distribution, [which is a good fit to the true spectrum](https://arxiv.org/abs/1211.3920). See `fluxes/sample-gamma.txt` for an unphysical sample file.

#### Princeton format
Used in [recent simulations](https://arxiv.org/abs/1804.00689) by the Princeton group.

#### Totani format
Used in [historical simulation by Totani et al.](https://arxiv.org/abs/astro-ph/9710203), which is the baseline model in the [Hyper-Kamiokande Design Report](https://arxiv.org/abs/1805.04163).


### Interaction Channels
Currently the four main interaction channels in water Cherenkov detectors are supported:
inverse beta decay, elastic scattering on electrons and charged current interactions of nu_e and anti-nu_e on oxygen-16 nuclei.
For details, see the files in `interaction_channels/`.


### Output
A .kin file in the NUANCE format used by the /mygen/vecfile options in WCSim. See [the format documentation](http://neutrino.phy.duke.edu/nuance-format/) for details.


### Typical Usage
```
python genevts.py fluxes/intp2001.data --format=nakazato -o outfile.kin --hierarchy=normal --channel=ibd
```

See
```
python genevts.py -h
```
for a full description of these and other options.

sntools currently uses Python 2.7, numpy 1.8 (or higher) and scipy 0.13 (or higher).
