# Running Quarto documents inside ShinyProxy

This repository describes how to add a [Quarto](https://quarto.org/) document
(with or without pre-rendering) inside ShinyProxy (at least version 2.5.0).

# Build the Docker image

To pull the image made in this repository from Docker Hub, use

```bash
sudo docker pull openanalytics/shinyproxy-quarto-demo
```

the relevant Docker Hub repository can be found at <https://hub.docker.com/r/openanalytics/shinyproxy-quarto-demo>.

To build the image from the Dockerfile, clone this repository, then navigate to its root directory and run

```bash
cd quartoDemo
sudo docker build -t openanalytics/shinyproxy-quarto-demo .
```

This repository also contains an example of a Quarto document that is
pre-rendered during the Docker build. This reduces the startup time of the
application. This image is available on Docker Hub:


```bash
sudo docker pull openanalytics/shinyproxy-quarto-demo:prerendered
```

To build the image:

```bash
cd quartoDemo_prerendered
sudo docker build -t openanalytics/shinyproxy-quarto-demo:prerendered .
```

# ShinyProxy Configuration

To add the quarto application (both with and without pre-render) to ShinyProxy,
add the following lines to its configuration file (
see [application.yml](./application.yml) for a complete file):

```yaml
proxy:
  specs:
    - id: quarto-demo
      display-name: Quarto Demo Application
      container-image: openanalytics/shinyproxy-quarto-demo
    - id: quarto-prerendered-demo
      display-name: Quarto Demo Application (prerendered)
      container-image: openanalytics/shinyproxy-quarto-demo:prerendered
```

## References

- <https://quarto.org/docs/get-started/hello/text-editor.html>
- [ShinyProxy.io](https://shinyproxy.io/)
- [All demos](https://shinyproxy.io/documentation/demos/)

**(c) Copyright Open Analytics NV, 2024.**
