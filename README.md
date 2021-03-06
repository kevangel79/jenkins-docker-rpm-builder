This is the repository for the docker based RPM builder that is used by ARGOeu. The RPM builder is meant to run by Jenkins as part of the continuous integration process. The repository includes

- the docker configuration for centos-6;
- configuration files for the extra rpm repositories;
- a docker configuration with the rpms required for building the ARGO rpm packages;
- the builder script that is executed as part of the Jenkins build pocess.

# Building the docker image

```bash
cd docker/centos-6-epel && docker build --pull -t centos-epel6dev-argoeu .
```

# Jenkins configuration

Clone the repository to ```${JENKINS_HOME}```:

```
git clone https://github.com/ARGOeu/jenkins-docker-rpm-builder.git dockers/argoeu
```

and add the following ```execute shell``` ```build step```:

```
cd ${WORKSPACE} && \
${JENKINS_HOME}/dockers/argoeu/rpm-builder.sh
```


