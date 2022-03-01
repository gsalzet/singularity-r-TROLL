BootStrap: docker
From: ubuntu:18.04

%labels
  Author Salzet Guillaume

%help
  This will run rcontroll and other utilities from R packages
  
%apprun R
  exec R "${@}"

%apprun Rscript
  exec Rscript "${@}"

%runscript
  exec R "${@}"

%post
  # Software versions
  export R_VERSION=4.1.2

  # Get dependencies
  apt-get update
  apt-get install -y --no-install-recommends \
    locales \
    gnupg \
    software-properties-common \
    apt-utils

  # Configure default locale
  echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
  locale-gen en_US.utf8
  /usr/sbin/update-locale LANG=en_US.UTF-8
  export LC_ALL=en_US.UTF-8
  export LANG=en_US.UTF-8

  # Install R
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
  add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/'
  apt-get update && DEBIAN_FRONTEND="noninteractive" TZ="America/New_York" apt-get install -y tzdata
  apt-get install -y --no-install-recommends --allow-unauthenticated \
    r-base \
    r-base-core \
    r-base-dev \
    r-recommended \
    r-base-html \
    r-doc-html \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libcairo2-dev \
    libxt-dev

  # Add a default CRAN mirror
  echo "options(repos = c(CRAN = 'https://cran.rstudio.com/'), download.file.method = 'libcurl')" >> /usr/lib/R/etc/Rprofile.site

  # Add a directory for host R libraries
  mkdir -p /library
  echo "R_LIBS_SITE=/library:\${R_LIBS_SITE}" >> /usr/lib/R/etc/Renviron.site

  # Clean up
  rm -rf /var/lib/apt/lists/*
  
  # Install r packages
  add-apt-repository ppa:cran/v8
  add-apt-repository ppa:cran/libgit2
  apt -f install
  apt update && apt dist-upgrade -y
  apt-get update -qq 
  apt-get install -y \
    --no-install-recommends \
    libudunits2-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libgdal-dev \
    libgsl-dev \
    libgit2-dev
  Rscript -e "install.packages('devtools', dependencies = c('Depends', 'Imports', 'LinkingTo'),repos='http://cran.us.r-project.org')" 

  Rscript -e "devtools::install_github('sylvainschmitt/rcontroll@dev',upgrade = 'always',force = TRUE, dependencies = c('Depends', 'Imports', 'LinkingTo'),repos='http://cran.us.r-project.org')" 
  Rscript -e "devtools::install_github('VincyaneBadouard/LoggingLab',upgrade = 'always',force = TRUE, dependencies = c('Depends', 'Imports', 'LinkingTo'),repos='http://cran.us.r-project.org')"
  Rscript -e "Sys.setenv(R_REMOTES_NO_ERRORS_FROM_WARNINGS="true")
devtools::install_github('ErikKusch/KrigR',upgrade = 'always',force = TRUE, dependencies = c('Depends', 'Imports', 'LinkingTo'),repos='http://cran.us.r-project.org')"
  Rscript -e "install.packages(c('tidyverse', 'sf', 'sp', 'hetGP', 'coda','entropart','fitdistrplus','ForestGapR','lhs'), dependencies = c('Depends', 'Imports', 'LinkingTo'),repos='http://cran.us.r-project.org')" 
  rm -rf /tmp/downloaded_packages/ /tmp/*.rds
