FROM python:3.5

ENV APP_DIR /srv/app

# Set the timezone.
RUN echo "Etc/UTC" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

RUN apt-get update && apt-get -y install -qq --force-yes cron nano supervisor rsyslog telnet

RUN mkdir -p /var/log/supervisor

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Configure cron.
COPY crontab /etc/cron.d/cron
RUN rm -Rf /etc/cron.daily  && \
    rm -Rf /etc/cron.weekly && \
    rm -Rf /etc/cron.monthly && \
    rm -Rf /etc/cron.hourly && \
    chmod 0644 /etc/cron.d/cron

# Create the log file to be able to run tail
RUN touch /var/log/cron.log

# add and make executable shell scripts that will be run by the cron
ADD cronjobs /usr/local/bin/

RUN chmod 0700 /usr/local/bin/hello.sh

# This just creates the folder in the Docker image at the
# install path we defined above.
RUN mkdir -p $APP_DIR

# By doing this, Docker will be smart enough to execute all
# future commands from within this directory.
WORKDIR $APP_DIR

CMD ["/usr/bin/supervisord"]
