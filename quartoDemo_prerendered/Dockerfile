FROM rocker/r-ver:4.2.3

# optionally use https://quarto.org/download/latest/quarto-linux-amd64.deb for the latest quarto version

RUN apt-get update && \
    apt-get install -y --no-install-recommends pandoc libxt6 curl ca-certificates && \
    curl -L -o quarto.deb https://github.com/quarto-dev/quarto-cli/releases/download/v1.4.549/quarto-1.4.549-linux-amd64.deb && \
    dpkg -i quarto.deb && \
    rm quarto.deb && \
    rm -rf /var/lib/apt/lists/*

RUN R -q -e "install.packages(c('rmarkdown', 'shiny', 'quarto'))"

RUN mkdir /app
WORKDIR /app

COPY quartoDemo.qmd .

RUN quarto render quartoDemo.qmd

EXPOSE 3838

CMD ["quarto", "serve", "quartoDemo.qmd", "--port", "3838", "--host", "0.0.0.0", "--no-render"]
