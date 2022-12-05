# neuro-images
Docker images for neuroimaging

## Images

- `base` contains the base image for the rest of the images included in this repository. It is a copy of [`continuumio/miniconda3`](https://hub.docker.com/r/continuumio/miniconda3) that uses `debian:buster` as a base image rather than `debian:latest` (see [here](https://hub.docker.com/r/continuumio/miniconda3/dockerfile) for original Dockerfile). This mainly ensures that `AFNI` can run (see [here](https://github.com/docker-library/python/issues/636#issuecomment-903976957) for related issues regarding `AFNI` and debian verisons). Copying `continuumio/miniconda3` was necessary to get `fsl` installed in subsequent images.
- `fsl` is the bare minimum neuroimaging image. As given by the name, it only installs FSL, which is useful for doing basic everyday neuroimaging tasks. It uses (and therefore depends on) `base` as the base image. 
- `fsl-afni` builds on top of the `fsl` image to also include `AFNI`. It uses `fsl` as the base image.


## Notes

- `--platform linux/amd64` is required for building images on MacOS with M1 chips.