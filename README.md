rcontroll Singularity container
================
Salzet Guillaume
February 28, 2022

**R, rcontroll and calibration packages**

Repository based on public template
[`sylvainschmitt/singularity-template`](https://github.com/sylvainschmitt/singularity-template)

This container includes:

-   `R` 4.1.2
-   `rcontroll` 0.1.0
-   `tidyverse` 1.3.1
-   `sf` 1.0-5
-   `sp` 1.4-6
-   `hetGP` 1.1.4
-   `coda` 0.19-4
-   `entropart` 1.6-8
-   `fitdistrplus` 1.1-6
-   `ForestGapR` 0.1.6
-   `lhs` 1.1.3
-   `LoggingLab` 0.0.0.9003

Singularity container based on the recipe:
[`Singularity`](https://github.com/gsalzet/singularity-r-TROLL/blob/main/Singularity)

Image singularity (V&gt;=3.6.4) is automatically test and built and
pushed on the registry using
[test.yml](https://github.com/gsalzet/singularity-template/blob/main/.github/workflows/test.yml)
&
[builder.yml](https://github.com/gsalzet/singularity-template/blob/main/.github/workflows/builder.yml)

Initial bootstrap :
[`docker://ubuntu:18:04`](https://hub.docker.com/_/ubuntu)

**build**:

``` bash
sudo singularity build Singularity TROLL_utilities.sif
```

**pull**:

``` bash
singularity pull https://github.com/gsalzet/singularity-template/releases/download/0.0.2/gsalzet-singularity-r-TROLL.latest.sif
```

**snakemake**:

``` python
    singularity: 
        "https://github.com/gsalzet/singularity-template/releases/download/0.0.2/gsalzet-singularity-r-TROLL.latest.sif"
```
