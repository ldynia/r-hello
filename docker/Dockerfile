FROM rocker/shiny:4.0.3

# install renv & restore packages
RUN Rscript -e 'install.packages("renv")'
RUN Rscript -e 'renv::consent(provided = TRUE)'
RUN Rscript -e 'renv::restore()'

WORKDIR /app
COPY ./ /app

# SSH setup
RUN apt-get update && apt-get install -y ssh
RUN echo "root:Docker!" | chpasswd && mkdir /run/sshd
COPY ./config/sshd_config /etc/ssh/

VOLUME /app/data

EXPOSE 80 2222 3838

CMD /app/scripts/startup.sh