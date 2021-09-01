# 📣 Protopia Open-source Demos

This repository contains a showcase of Protopia technology, packaged in convenient container images. Go on and give it a try!

## Cloak Face Detection
The Cloak Face Detection demo illustrates a simple face detecting neural network with and without _Cloak_, the Protopia's secure privacy preserving noise generation technology. 
The demo is packaged as a container image that contains all the dependencies you need to see Cloak in action. The image allows a user to provide an image as input and see the faces detected in it with and without Cloak noise.

For example, the image below shows the face detection inference applied on two images: the original image without Cloak noise on the left, and Cloak noise added on the right. In both images the detected faces are highlighted using red squares. Here, we can see how Cloak allows the face detection model to remain useful while revealing _just enough information_ for the model to do its job.

![Cloak Face Detection Example Output](docs/images/cloak-fd-output.png)

Try it out for yourself; grab your selfie stick and see how Cloak preserves your privacy and security by adding just enough noise your image revealing only enough information for the face detection model to do its job :tada:

### Usage

First things first make sure you have Docker installed on your machine, and it is up and running. See instructions [here](https://docs.docker.com/get-docker/) on how to install Docker. You can use other container runtime environments if you wish; the usage guide here is written for Docker.

<!-- START: TO BE REMOVED ONCE REPO IS PUBLIC -->

_Since we have not released this demo publicly yet, the image is stored in a private container registry. For that reason we need to authenticate Docker so that it call pull the demo image. Once the demo is released publicly, we no longer need this step and will remove this section. To authenticate Docker so that it can pull the private demo image, follow the instructions [here](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#authenticating-to-the-container-registry)._

<!-- END: TO BE REMOVED ONCE REPO IS PUBLIC -->

Once Docker is installed, pull the latest Protopia demo by running:

```shell script
docker pull ghcr.io/protopia-ai/demo:latest
```

Grab your selfie stick and take a picture. If you don't have that handy, don't worry; any picture with faces on it would work :blush: Place the picture in a directory. Let's assume the picture's file name is `input.png`. 

Open up the terminal, and `cd` into the directory that contains the `input.png` picture. Now the fun part: run the demo and see the comparison of input images with-and-without Cloak noise added by running:

```
 docker run -v $PWD:/data ghcr.io/protopia-ai/demo:latest -i /data/input.png -o /data/output.png
``` 

Let's break down what this command does:
1. `docker run` runs a given container for us using Docker container runtime.
1. `-v $PWD:/data` mounts the current working directory onto `/data` on the container. This allows the container to see the `input.png` picture in the current directory and write the output picture into it.
1. `ghcr.io/protopia-ai/demo:latest` is the name of the container image we are running.
1. `-i /data/input.png` tells the demo where to find the input image. Remember, we have mounted current working directory onto `/data` in the container. So the input picture within the container would be at `/data/input.png`.
1. `-o /data/output.png` tells the demo where to write out the side-by-side comparison of AI with-and-without Cloak. We write the image into the same `/data` directory so that it shows up in the current working directory.

Easy peasy!

Running the command above will generate `output.png` in the current working directory. 

Congratulations! :confetti_ball: You have just used Protopia's Cloak technology to preserve the privacy and security of your input data while keeping AI useful :raised_hands:
