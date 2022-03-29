FROM datashield/rstudio-jupyter:1.2.0

USER root

RUN apt update && apt install -y r-base-dev

# Install BioConductor symlink for littler
RUN ln -s /opt/conda/lib/R/library/littler/examples/installBioc.r /usr/local/bin/installBioc.r 

# Install dsOmicsClient dependencies
ENV BIOCMANAGER_VERSION "v1.30.16"
RUN installGithub.r "Bioconductor/BiocManager@${BIOCMANAGER_VERSION}"

# Install OS deps for dsOmicsClient
RUN apt install libfftw3-dev
RUN conda install -c conda-forge fftw 

# Install dsOmicsClient
ENV DSOMICS_VERSION "1.0.8"
RUN installGithub.r "isglobal-brge/dsOmicsClient@${DSOMICS_VERSION}"

USER ${NB_USER}

CMD ["/usr/lib/rstudio-server/bin/rserver", "--server-daemonize", "0", "--auth-none", "1", "--www-frame-origin", "same", "--www-verify-user-agent", "0"]