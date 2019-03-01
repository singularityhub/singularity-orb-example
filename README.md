# Singularity Orb Example

This is a basic example of the [Circle CI Orb](https://circleci.com/orbs/registry/) to help you 
interact with [Singularity containers](https://www.github.com/sylabs/singularity).
The orb is published at [singularity/singularity](https://circleci.com/orbs/registry/orb/singularity/singularity).

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

The basic example here is found in the [.circleci/config.yml](.circleci/config.yml) file.
This is the fastest way to build a container, and will default to Singularity 3.1.0.

```yaml
version: 2.1

orbs:
  singularity: singularity/singularity@dev:alpha

workflows:
  build_container_docker_base_example:
    jobs:
      - singularity/build_container_docker_base:
          from-uri: docker://busybox 
          image: busybox.sif 
          filters:
            branches:
              only: master
```

### How do I...

I will write more documentation and examples at the request of users, so please
ask if you would like an example for your purposes. For full examples,
see the [singularityhub/singularity-orb](https://www.github.com/singularityhub/singularity-orb) repository.
