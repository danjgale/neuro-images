# FSL 

Docker image with only FSL installed. This image serves as a base image for subsequent images, as I pretty much rely on FSL for everyday neuroimaging. 

## Build

Command: 
`docker build -t fsl .`

## Notes

- `--platform linux/amd64` is required to build image on MacOS with M1 chips.
- `continuumio/miniconda3` is used as the base image because it is the only image I have been able to get working with FSL.
- There are tons of known issues with FSL and docker. This seems to work for 6.0.6, but not earlier versions.  