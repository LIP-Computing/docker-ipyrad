# Docker: ipyrad

Docker to run ipyrad

Installation and user manual is found here:
* http://ipyrad.readthedocs.io/index.html

Tags correspond to the version of ipyrad, currently:

* latest: ipyrad 0.7.9

## Usage udocker

udocker is a user client tool to run docker containers without docker.
It's aimed at running applications in user space without root or admin previledges.

udocker resources can be found in:

* Repository: https://github.com/indigo-dc/udocker
* Installation manual: https://github.com/indigo-dc/udocker/blob/master/doc/installation_manual.md
* User manual: https://github.com/indigo-dc/udocker/blob/master/doc/user_manual.md
* Paper open access: https://doi.org/10.1016/j.cpc.2018.05.021

A summary of using udocker to run ipyrad follows:

    mkdir -p ~/bin
    curl https://raw.githubusercontent.com/indigo-dc/udocker/master/udocker.py > bin/udocker
    chmod u+rx bin/udocker
    udocker install
    udocker pull lipcomputing/ipyrad:0.7.30
    udocker create --name=ipyrad lipcomputing/ipyrad:0.7.30

If you are running with multiple threads or processes, OpenMP or OpenMPI, better
performace is acheived with udocker F mode:

    udocker setup --execmode=F1 ipyrad

If you have input files to pass to the container to run the application, for
example in `~/input`, you can run:

    udocker run -v  $PWD/input:/home ipyrad ipyrad -n iptest


## Usage Docker

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
