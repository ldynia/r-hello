FROM rocker/shiny:4.0.3

WORKDIR /app

COPY ./ /app

RUN rm -rf /srv/shiny-server/

# install renv & restore packages
RUN Rscript -e 'install.packages("renv")'
RUN Rscript -e 'renv::consent(provided = TRUE)'
RUN Rscript -e 'renv::restore()'

VOLUME /app

EXPOSE 3838

CMD ["R", "-e", "shiny::runApp('/app', host = '0.0.0.0', port = 3838)"]
