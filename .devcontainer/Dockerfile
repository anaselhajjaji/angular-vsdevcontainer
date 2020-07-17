FROM node:lts

EXPOSE 4200

# Configure apt
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
  && apt-get -y install --no-install-recommends apt-utils 2>&1

# Verify git and needed tools are installed
RUN apt-get -y install --no-install-recommends git procps net-tools curl

# Install the Angular CLI
RUN npm install -g @angular/cli

# Clean up
RUN apt-get clean && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/apt && \
  npm cache clean --force

# Disable Angular CLI prompt
ENV NG_CLI_ANALYTICS="ci"

CMD [ "/bin/bash" ]