# Run Inkscape using Docker

Download Inkscape from Docker Hub and store it locally on your machine:
```bash
docker pull haggaie/inkscape
```

After pulling the image, you can use it to create and run containers based on the Inkscape image called **haggaie/inkscape**.

Before running the container don't forget to run:

```bash
xhost +local:root
```

This will allow to run GUI applications in Docker on Linux hosts.

Finally you can run the container:

```bash
docker run --rm -it -v /tmp/.X11-unix:/tmp/.X11-unix -v /$HOME/Documents/Inkscape:/Inkscape -e DISPLAY=unix$DISPLAY haggaie/inkscape
```

Note: We can see that we have created a volume so that we can save, import or export files from our host machine to Docker.

Also if you want to run it as Host User:

```bash
docker run --rm -it -u $(id -u):$(id -g) -v /tmp/.X11-unix:/tmp/.X11-unix -v /$HOME/Documents/Inkscape:/Inkscape -e DISPLAY=unix$DISPLAY haggaie/inkscape
```