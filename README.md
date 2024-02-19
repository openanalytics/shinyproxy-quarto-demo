# Running Quarto documents inside ShinyProxy

This repository describes how to add a Quarto document inside ShinyProxy (at least version 2.5.0).

# Build the Docker image

To pull the image made in this repository from Docker Hub, use

```
sudo docker pull openanalytics/shinyproxy-quarto-demo
```

the relevant Docker Hub repository can be found at https://hub.docker.com/r/openanalytics/shinyproxy-quarto-demo

To build the image from the Dockerfile, clone this repository, then navigate to its root directory and run

```
sudo docker build -t openanalytics/shinyproxy-quarto-demo .
```

# ShinyProxy Configuration

To add the quarto application to ShinyProxy add the following lines to its configuration file (see [application.yml](./application.yml) for a complete file):
```
specs:
  - id: quarto-demo
    display-name: Quarto Demo Application
    container-image: openanalytics/shinyproxy-quarto-demo
```

# References
* https://quarto.org/docs/get-started/hello/rstudio.html


**(c) Copyright Open Analytics NV, 2024.**