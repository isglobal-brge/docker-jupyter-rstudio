# RStudio - with dsExposomeClient
Based upon [datashield/rstudio-jupyter](https://hub.docker.com/r/datashield/rstudio-jupyter). Extended with the dsExposome client environment.

## Contents
The exposome environment is pre-installed on the RStudio.
- [dsBaseClient](https://github.com/datashield/dsBaseClient)
- [dsExposomeClient](https://github.com/isglobal-brge/dsExposomeClient)

## Build
To build the needed images you need to exceute the following command:

```bash
docker build . -t brgelab/rstudio-jupyter-exposome:*major-version* -t brgelab/rstudio-jupyter-exposome:latest -t brgelab/rstudio-jupyter-exposome:*specific-tag*
# example
docker build . -t brgelab/rstudio-jupyter-exposome:2 -t brgelab/rstudio-jupyter-exposome:latest -t brgelab/rstudio-jupyter-exposome:2.0.3
```

## Release
You can publish to dockerhub using the `docker push`.

`docker push brgelab/rstudio-jupyter-exposome`

## Usage
You can use the image locally as well. Run the following snippet:

`docker run -p 8787:8787 brgelab/rstudio-jupyter-exposome:2 -d`

You can access rstudio on http://localhost:8787
### Authentication
We authenticate with the central authentication mechanism of [MOLGENIS](https://molgenis.org) and [ELIXIR](https://elixir-europe.org/services/compute/aai).