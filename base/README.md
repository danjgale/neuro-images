# base 

Base image for all other images in repository. It is a copy of `continuumio/miniconda3` that uses `debian:buster` instead of `debian:base` for the base image.

Original `continuumio/miniconda3` Dockerfile found [here](https://hub.docker.com/r/continuumio/miniconda3/dockerfile). 

## Build

Command:
`docker build -t base .`