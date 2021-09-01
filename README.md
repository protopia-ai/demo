# :mega: Protopia AI Demo
This repository provides a way for you to test your own image files with the Protopia AI solution. You’ll see how simple and effortless this process is to minimize the AI Data that is used on a need-to-know basis. Through our patented technology, Protopia masks away any information that is not specifically required to complete an inference task. Go on and give it a try!

Note: Our solution works with a variety of data types. Contact us at jake@protopia.ai if you want to test your own model.

## Cloak Face Detection
This demo illustrates a face-detecting deep neural network with and without _Cloak_, Protopia's secure privacy preserving noise generation technology. The demo is packaged as a container image that contains all the dependencies you need to see Cloak in action. The demo allows you to provide an image as input and see the faces detected in it with and without Cloak noise.

For example, the image below shows the face detection inference applied on two images: the original image without Cloak noise on the left, and Cloak noise added on the right. In both images, the detected faces are highlighted using red squares. Here, we can see how Cloak allows the face detection model to remain useful while revealing _just enough information_ for the model to do its job.


![Cloak Face Detection Example Output](docs/images/cloak-fd-output.png)

Try it out for yourself; grab your selfie stick and see how Cloak preserves your privacy and security by adding noise to a degree that only reveals enough information for the face detection model to do its job :tada:

### Usage

First things first, make sure you have Docker installed on your machine, and it is up and running. See instructions [here](https://docs.docker.com/get-docker/) on how to install Docker. You can use other container runtime environments if you wish; the usage guide here is written for Docker.

Once Docker is installed, pull the latest Protopia demo by running:

```shell script
docker pull ghcr.io/protopia-ai/demo:latest
```

Grab your selfie stick and take a picture. If you don't have that handy, don't worry; any picture with faces on it will work :blush: Place the picture in a directory. Let's assume the picture's file name is `input.png`. 

Open up the terminal, and `cd` into the directory that contains the `input.png` picture. Now the fun part: run the demo and see the comparison of input images with-and-without Cloak noise added by running:

```
 docker run -v $PWD:/data ghcr.io/protopia-ai/demo:latest -i /data/input.png -o /data/output.png
``` 

Let's break down what this command does:
1. `docker run` runs a given container for us using Docker container runtime.
1. `-v $PWD:/data` mounts the current working directory onto `/data` on the container. This allows the container to see the `input.png` picture in the current directory and write the output picture into it. However, all the paths inside the docker container are expressed with respect to the `/data` mounted virtual drive.
1. `ghcr.io/protopia-ai/demo:latest` is the name of the container image we are running.
1. `-i /data/input.png` tells the demo where to find the input image. Remember, we have mounted current working directory onto `/data` in the container. So the input picture within the container is only refrencable at `/data/input.png`.
1. `-o /data/output.png` tells the demo where to write out the side-by-side comparison of the result of deep neural network with-and-without Cloak. We write the image into the same `/data` virtual mount point so that it shows up in the current working directory.

That was easy!

Running the command above will generate `output.png` in the current working directory. 

Congratulations! :confetti_ball: You have just used Protopia's Cloak technology to preserve the privacy and security of your input data while keeping AI useful :raised_hands:

**Note:** Our solution works with a variety of data types. Contact us at jake@protopia.ai if you want to test your own model.
