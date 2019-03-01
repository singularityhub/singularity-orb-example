# Singularity Orb Example

This is an example of the [Circle CI Orb](https://circleci.com/orbs/registry/) to help you 
interact with [Singularity containers](https://www.github.com/sylabs/singularity).

## Usage

### Configure

Fork or otherwise clone / copy the repository here, or as an alternative
just copy the [.circleci/config.yml](.circleci/config.yml) file to
your repository.

### Customize

Customize the file with your build recipe, and name. There is a very basic
example in the file itself. If you want a custom example then 
[open an issue](https://www.github.com/singularityhub/singularity-orb-example)
and I'll write it for you! 

#### What can I customize?

You can generally customize:

 - the Singularity version
 - the container name
 - the from uri (e.g., docker:// versus a Singularity recipe)


### Examples

The examples below describe the `.circleci/config.yml` file in your repository!
Here is a very basic example to build a container - this will use the
default Singularity version 3.1. 

```yaml
version: 2.1

orbs:
  singularity: singularity/singularity@1.0.1

workflows:
  build_example:
    jobs:
      - singularity/build_container:
          from-uri: docker://busybox 
          image: busybox.sif 
```

You can also specify a custom version of Singularity (this corresponds to
the version that you would clone from GitHub - the builder will use a go
base docker image and install Singularity to it:

```yaml
version: 2.1

orbs:
  singularity: singularity/singularity@1.0.1

workflows:
  build_example:
    jobs:
      - singularity/build_container:
          singularity-version: 3.0.2
          from-uri: docker://busybox 
          image: busybox.sif 
```

But if you want to just use a Docker container from [singularityware/singularity](https://hub.docker.com/r/singularityware/singularity/tags)
the job name that you want is `singularity/build_container_docker` and the default `singularity-version` corresponds to `3.1-slim`.

```yaml
version: 2.1

orbs:
  singularity: singularity/singularity@1.0.1

workflows:
  build_example:
    jobs:
      - singularity/build_container_docker:
          from-uri: docker://busybox 
          image: busybox.sif 
```

*This is the fastest way to build!*

Finally, if you want an older version of Singularity (pre GoLang) you want to do this:

```yaml
version: 2.1

orbs:
  singularity: singularity/singularity@1.0.1

workflows:
  build_example:
    jobs:
      - singularity/build_container_version_2:
          from-uri: docker://busybox
          image: busybox.sif 
```

The default `singularity-version` is 2.6.1, again corresponding to the [Github tag](https://github.com/sylabs/singularity/releases).

### How do I...

I will write more documentation and examples at the request of users, so please
ask if you would like an example for your purposes.


