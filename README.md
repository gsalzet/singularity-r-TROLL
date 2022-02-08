Template Singularity container
================
Salzet Guillaume
February 07, 2022

**rcontroll package Template**

Template is a set of utilities that allow to use rcontroll.

Template Version: X.X.X

\[URL\]

Singularity container based on the recipe: Singularity

Package installation using Miniconda3 V4.7.12

Image singularity (V\>=3.3) is automatically test and built and pushed
on the registry using
[test.yml](https://github.com/sylvainschmitt/singularity-template/blob/main/.github/workflows/test.yml)
&
[builder.yml](https://github.com/sylvainschmitt/singularity-template/blob/main/.github/workflows/builder.yml)

**build**:

``` bash
sudo singularity build Singularity img.sif
```

**pull**:

``` bash
singularity pull https://github.com/gsalzet/singularity-template/releases/download/0.0.1/gsalzet-singularity-template.latest.sif
```

**snakemake**:

``` python
    singularity: 
        "https://github.com/gsalzet/singularity-template/releases/download/0.0.1/gsalzet-singularity-template.latest.sif"
```
