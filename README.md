`ijulia-notebook` is a JupyterLab/Jupyter Notebook container which
includes the IJulia (https://github.com/JuliaLang/IJulia.jl)
kernel.

This container is intended to be a more minimal, Julia-focused
alternative to `jupyter/datascience-notebook`. It is built on top of
`jupyter/minimal-notebook`, and includes a few useful Julia packages
such as Makie. It doesn't include any extra packages for Python or
other languages.

# Building
```
$ podman build --format=docker -t ijulia-notebook .
```

# Running
```
podman run -d \
       --name=jupyter \
       --publish=8888:8888 \
       --userns=keep-id \
       --mount type=bind,src=$HOME/notebooks,dst=/home/jovyan/work \
       localhost/ijulia-notebook
```
