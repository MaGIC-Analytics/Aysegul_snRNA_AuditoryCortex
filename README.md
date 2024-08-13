# Aysegul_snRNA_AuditoryCortex Project
![GitHub last commit](https://img.shields.io/github/last-commit/MaGIC-Analytics/Aysegul_snRNA_AuditoryCortex)
[![run with docker](https://img.shields.io/badge/run%20with-docker-0db7ed?labelColor=000000&logo=docker)](https://www.docker.com/)
[![run with singularity](https://img.shields.io/badge/run%20with-singularity-1d355c.svg?labelColor=000000)](https://sylabs.io/docs/)
[![run with RStudio](https://img.shields.io/badge/RStudio-75AADB?style=for-the-badge&logo=RStudio&logoColor=white)](https://posit.co/products/open-source/rstudio/)
[![made with Shiny](https://img.shields.io/badge/R-Shiny-blue)](https://shiny.rstudio.com/)

## Description
This is the code repository for the project with Aysegul Gungor Aydin and Kasia Bieszczad for interogating the single nuclei composition of the auditory cortex. All communications regarding the final publication should be addressed to the corresponding author. 

## Execution
To execute this data, you can use a docker container with the preloaded libraries. Due to the relativistic nature of UMAP, your plots may generate slightly different so double check the reclustering matches the appropriate populations. The final conclusions should be identical (or nearly). 

```bash
docker run --rm -p 8787:8787 -e PASSWORD=${password} -v ~./analysis:/home/rstudio alemenze/abrfseurat:v1
```
This will run an Rstudio instance on your local machine using our prebuilt docker container version that was used for processing this data. You must define a password for the rstudio environment, and change the local directory to the appropriate path of your input data. From there, you can navigate in your browser to [localhost:8787](http://localhost:8787), and access the rstudio environment. 

Then you can follow along with the rmarkdown file provided. 

## Input Data
Input data was raw .h5 matrices generated from cellranger v6. Raw fastq files and raw .h5 matrices can be found at the Gene Expression Omnibus at accession [GSE262970](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE262970)

## Data exploration
For ease, this data has also been built into a containerized RShiny image that can be launched on a local machine. To do so, you must have [docker](https://www.docker.com/) installed locally. Once installed, this can be launched:
```bash
docker run --rm -p 8080:8080 alemenze/auditory-cortex-visualizer
```
and it should be hosted at [localhost:8080](http://localhost:8080/). You can switch this to whatever port works with your system, but 8080 is the default we use for shiny apps. 