# DnnDevEnvOnWSL
> Make Deep learning environment on WSL easily and fastly.

This is a wsl image for quick development environment configuration and flexibility in a Windows environment.

Through this, it is possible to support GPU use in Tensorflow or JAX, which could not be used with Docker alone.

Additionally, CUDA installation, which requires a considerable amount of time and effort, is also performed automatically, saving time and effort.

## How to start
There are two installation methods. The easiest way is to use a pre-built image, but you can also personalize it by modifying the Dockerfile yourself.

### Get start from prebuilt image

```powershell
wsl --set-default-version 2
wsl --import {distro_name} {install_dir} {distro_name}.tar.gz
wsl -d {distro_name}
```

`distro_name` is the prebuilt image's name.
`install_dir` is a location to store vm image for wsl.

### Get start from Dockerfile

```powershell
docker build --build-arg USER={user_name} --build-arg PASSWD={pass word} -t {distro_name} .
docker run --name {distro_name} {distro_name}
docker export --output="{distro_name}.tar.gz" {distro_name}

...
```

It is similar with general Dockerfile usage.
The tasks performed after exporting the image to a tar.gz file are the same as using a “prebuilt image”.

### Remove the environment

```powershell
wsl --unregister {distro_name} # unregister distro
```

After unregister from wsl, delete the directory created in the process of registering with wsl.

## References
- https://medium.com/nerd-for-tech/create-your-own-wsl-distro-using-docker-226e8c9dbffe
- https://learn.microsoft.com/ko-kr/windows/wsl/basic-commands