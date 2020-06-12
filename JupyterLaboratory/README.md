# Jupyter Lab on Docker

## Preparation
```
mkdir ~/WorkSpace
```

## Docker Run
`docker run --rm -p 8888:8888 -v ~/WorkSpace/JupyterLaboratory/src:/work --name JupyterLab-on-Docker yuta0601/jupyter-lab:latest`

## Access
`localhost:8888`