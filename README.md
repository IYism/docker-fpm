# FPM Docker Image

## About
Effing Package Management (FPM) is a tool that simplifies the process of building packages for multiple platforms, including Debian (deb), Red Hat (rpm), and others, with ease and sanity. This Docker image is based on Rocky Linux 9 and provides a convenient environment for using FPM to create packages.

For more information on FPM and its usage, visit the official documentation: [FPM Documentation](https://fpm.readthedocs.io/en/latest/)

## Components

* **Ruby**: Version `3.2.5`
* **fpm**: Version `1.15.1`

## Quick Start

### Build the Docker Image
Build the Docker image locally:
```sh
docker build -t fpm:latest .
```

### Run the Container
You can run the FPM container using the following command, which will output the FPM version by default.
```sh
docker run --rm -it fpm
```

### Example Usage
To customize the RPM package creation, you can mount your own source files and specify an output directory for the generated RPM. Here’s how to run the Docker container with FPM:
```sh
docker run --rm -it \
    -v /your/src/path:/src  \
    -v /your/rpm/path:/output \
    fpm:latest \
    fpm \
    -f \
    -s dir \
    -t rpm \
    -n appname \
    --epoch 0 \
    -v 1.0.0 \
    --iteration 1 \
    --rpm-dist el9 \
    -a 'x86_64' \
    -m 'iYism' \
    --vendor 'iyism inc.' \
    --category 'System Environment/Daemons' \
    --license 'MIT License' \
    --rpm-summary 'A simple application' \
    --description 'A simple hello world application.' \
    --url 'https://github.com/IYism' \
    --verbose \
    -C /src \
    --package /output
```

### Contributing
Feel free to submit issues or pull requests to enhance the functionality of this Docker image.

### License
This project is licensed under the MIT License.
