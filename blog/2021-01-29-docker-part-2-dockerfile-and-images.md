---
title: Docker - Part 2 - Dockerfile & Images
path: docker-part-2-dockerfile-and-images
date: 2021-01-29
tags: ['coding', 'docker']
---

<h2> What is a Dockerfile? </h2>

A Dockerfile is a set of instructions on what Docker needs to know to build an image that will be used to create a new container.

<h2> Make-up of a Dockerfile </h2>

To make one, you just create a new file in the root of your project and name it "Dockerfile" (no extension).

There are various optional commands you can use. I'm just listing the ones I've learned so far:

- `FROM <image>[:<tag>]` can start you off with an existing image as the base of the build. In Docker Hub (we'll get to this in a bit), there are specific images that you can use like `node` or `python` for running programs based in that language.

- `WORKDIR path/to/folder` is the name of the directory being created in the container.

- `RUN <command>` launches necessary commands to run the program as you would do locally (for example: to install dependencies in a node project, you'd have to include `RUN npm install`).

- `COPY <path/to/source> <path/to/destination>` will copy the rest of the project's code into the image. There are 2 arguments for this command. The first being the path where the files are located on your computer, and the second being what path in the image it's being copied to.

- `EXPOSE <port>` is used to specify what ports the container should listen to when running. The port is expected in the project's code. This command is optional here and isn't required to run the container. This is just to show as documentation. What's important is publishing the port when running the container.

- `CMD ["<executable>", "<param1>", ...]` is the command to execute the project. There is only one of these instructions in the file. This won't be executed when the _image_ is created but when the _container_ is created.

<h2> What is an Image? </h2>

An image are the blueprints to make a container that contain code and required tools. One image can create multiple containers. Images can be shared so a developer can spin up a new container on their own machine without having to need the Dockerfile it was built from (of course this can be shared too).

<h2> Building an Image </h2>

Use the `docker build` command with the path where the Dockerfile is located.

Here, the `.` means the root of the folder.

```bash
> docker build .
```

After it's done building, there will be an ID created for the image to use to run a container. I found it easier to look under `docker images` to copy/paste this ID. This command will display all created images available.

Example:

```bash
> docker images
REPOSITORY               TAG                 IMAGE ID            CREATED             SIZE
<none>                   <none>              bee345bd2248        9 minutes ago       946MB
docker/getting-started   latest              67a3629d4d71        2 days ago          27.2MB
```

If you change the project's code after building the image, you will need to rebuild the image again. That's because images are read-only and locked once they're created. The `COPY` command takes a snapshot of the code and does not update itself if the project is edited.

<h2> Using Prebuilt Images </h2>

There are existing images you can use as a starter in a Dockerfile or just to use to solely run a container off of. [Docker Hub](https://hub.docker.com/) is a good source for finding images. Docker Hub is a lot like GitHub except it has images instead of repositories.

If you want to start up a new container (which will be discussed in the next section) you could use an image on Docker Hub as if it was already on your computer. Here, the `node` image is pulled from Docker Hub (if you're connected) since it's not on my computer. It will first look for the `node` image locally before searching Docker Hub.

The `docker run` command builds a new container.

```bash
> docker run node
```

[Found a typo or problem? Edit this page.](https://github.com/Dana94/website/blob/master/blog/2021-01-29-docker-part-2-dockerfile-and-images.md)
