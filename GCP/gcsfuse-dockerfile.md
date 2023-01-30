Implementing GCSfuse in dockerfile: 

In Dockerfile:

```
#install prerequisites for gcsfuse
RUN apt-get update -qq \
  && apt-get install -y --no-install-recommends --allow-unauthenticated curl gnupg

#install gcsfuse
RUN echo "deb http://packages.cloud.google.com/apt gcsfuse-bionic main" | tee /etc/apt/sources.list.d/gcsfuse.list \
  && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
  && apt-get update \
  && apt-get install -y gcsfuse
```

The container needs to run with “--privileged” switch and Inside the container, you need to run this in a startup shell script:

```
gcsfuse --only-dir directory-in-the-bucket gcs-bucket-name /local/path/to/mount/to
```

The –only-dir switch can be skipped and you can mount the whole bucket. 
