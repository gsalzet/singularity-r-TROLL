BootStrap: shub
From: tpall/singularity-r:latest

%labels
  Author Salzet Guillaume

%help
  This will run rcontroll and other utilities from R packages

%post
  apt-get update -qq \
    && apt-get install -y \
    --no-install-recommends \
    libudunits2-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libgdal-dev \
    libgsl-dev \
    libnode-dev \
    && Rscript -e "install.packages(c('tidyverse', 'sf', 'sp', 'hetGP', 'devtools', 'coda','entropart','fitdistrplus','Rcpp'), dependencies = c('Depends', 'Imports', 'LinkingTo'))" \
    && Rscript -e "devtools::install_github('sylvainschmitt/rcontroll@dev')" \
    && rm -rf /tmp/downloaded_packages/ /tmp/*.rds
