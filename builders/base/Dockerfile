# Use the base gcloud image, based on ubuntu:trusty
FROM gcr.io/cloud-docs-samples/gcloud

# Install updates and dependencies
RUN apt-get update -y && \
    apt-get install --no-install-recommends -y -q curl python build-essential git ca-certificates libkrb5-dev imagemagick && \
    apt-get clean && \
    rm /var/lib/apt/lists/*_*

# Install the latest LTS release of nodejs
RUN mkdir /nodejs && curl https://nodejs.org/dist/v6.10.2/node-v6.10.2-linux-x64.tar.gz | tar xvzf - -C /nodejs --strip-components=1
ENV PATH $PATH:/nodejs/bin

# Install the Repo Tools binary
RUN curl -O https://storage.googleapis.com/cloud-docs-samples/releases/latest/nodejs-repo-tools-linux \
    && mv ./nodejs-repo-tools-linux /usr/local/bin/samples \
    && chmod +x /usr/local/bin/samples
ENV PATH $PATH:/usr/local/bin

ENTRYPOINT ["gcloud"]
