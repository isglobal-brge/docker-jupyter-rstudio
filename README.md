# Jupyter Notebook RStudio containers
We are using Jupyter Notebooks to configure the different clients of DataSHIELD packages used in the projects we serve.

Currently we support these analysis environments:

Production
- DataSHIELD exposome environment [dsExposomeClient](https://github.com/isglobal-brge/dsExposomeClient)
- DataSHIELD omics environment [dsOmicsClient](https://github.com/isglobal-brge/dsOmicsClient)

You can you these images to support different analysis environments on the JupyterHub.

## Development
We define 2 environment in development of these images.

- production == R-packages can be used as production environments on JupyterHub
- development == R-packages are not released yet and/or work only with the development version of the dsBaseClient or other packages

## Building and publishing
We use [semantic release](https://github.com/semantic-release/semantic-release) to build and release the images.

## Usage

### Persist your installed R-libraries over different profiles
> **BE ADVISED**: these packages are tightly bound to a specific R-version. 
> If the RStudio is upgraded and another R-version is used as a base versions, these installed packages need to be reinstalled!

#### Create the R user library (only once)
1. You start a profile, for example DataSHIELD 6.1.0.
2. Open the RStudio via New --> RStudio
3. Create **only once** the directory `R/userlib` in your home directory
4. Add your own user library to the defaults
   ```
   userlib <- paste0(getwd(), '/R/userlib')
   .libPaths(userlib)
   ```

#### Install packages in the user library
1. Install a package and specify the library location
2. For example
   ```
   install.packages('dplyr', lib = '~/R/userlib')
   ```
   **The library location needs to be exactly this**

#### Add your own user library to the defaults
*You need to do this each time you load RStudio to be able to use it*
```
userlib <- paste0(getwd(), '/R/userlib')
.libPaths(userlib)
```
Now you can use preinstalled packages.
   
