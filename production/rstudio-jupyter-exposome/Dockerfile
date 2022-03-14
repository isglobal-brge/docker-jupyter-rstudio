FROM datashield/rstudio-jupyter:1.2.0

USER root

RUN apt update && apt install -y r-base-dev libudunits2-dev libgdal-dev libgeos-dev libproj-dev cmake

# Install BioConductor symlink for littler
RUN ln -s /opt/conda/lib/R/library/littler/examples/installBioc.r /usr/local/bin/installBioc.r 

# Install dsExposome dependencies
ENV BIOCMANAGER_VERSION "v1.30.16"
RUN installGithub.r "Bioconductor/BiocManager@${BIOCMANAGER_VERSION}"
RUN installBioc.r S4Vectors

# Install dsBaseClient
ENV DS_DEP_VERSION "6.1.1"
RUN installGithub.r "datashield/dsBaseClient@${DS_DEP_VERSION}" --deps=TRUE

# Install dsExposomeClient
ENV DS_PKG_VERSION "2.0.1"
RUN conda install r-units r-sf
RUN installGithub.r "isglobal-brge/dsExposomeClient@${DS_PKG_VERSION}" --deps=TRUE 

USER ${NB_USER}

CMD ["/usr/lib/rstudio-server/bin/rserver", "--server-daemonize", "0", "--auth-none", "1", "--www-frame-origin", "same", "--www-verify-user-agent", "0"]
