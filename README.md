# Docker: ipyrad

Docker to run ipyrad

Installation and user manual is found here:
* http://ipyrad.readthedocs.io/index.html

Tags correspond to the version of ipyrad, currently:

* latest: ipyrad 0.7.9

## Usage

Pull the docker image

```
docker pull lipcomputing/ipyrad
```

Run ipyrad: get the help usage

```
docker run lipcomputing/ipyrad ipyrad -h
```

Or you can run the container in interactive mode:

```
docker run -it lipcomputing/ipyrad /bin/bash

# ipyrad -h
```

Other examples in: http://ipyrad.readthedocs.io/outline.html 

You can map a directory into the docker container for input and output

If you local dir is `pwd`, you can run:

```
PWD=`pwd`
docker run -it -v ${PWD}:/home/test lipcomputing/ipyrad /bin/bash
# cd /home/test
```

Such that if you have you input files in your host machine, they will be
available in the directory `/home/test` inside the container, as well as
output files produced in that dir by running the application inside the container
they will be available when you exit, in that directory `pwd`.

## License

GNU GPL v3

## Author Information

Mario David: <mariojmdavid@gmail.com>

LIP Lisbon: http://www.lip.pt

Indigo DataCloud: https://www.indigo-datacloud.eu/
