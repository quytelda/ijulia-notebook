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

The simplest way to run the container is with `podman run -p 8888:8888
ijulia-notebook`. However, you probably want to define a volume or
bind mount for your saved notebooks so they will be preserved across
updates. For example, to run the container with a storage volume:
```
podman run --name=jupyter \
           --publish=8888:8888 \
           --volume=notebooks:/home/jovyan/work \
           localhost/ijulia-notebook
```
