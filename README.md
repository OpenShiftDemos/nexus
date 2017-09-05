# Sonatype Nexus on OpenShift

This repo contains an OpenShift template for deploying Sonatype Nexus 3 in OpenShift. This is a fork of the [OpenShiftDemos/nexus][demorepo] repository, with some customisations to the memory settings, deployment strategy and ports, for the purposes of a tutorial article.

# Import Templates

In order to add Sonatype Nexus templates to OpenShift service catalog run the following commands:

Sonatype Nexus 3:
```
oc create -f https://raw.githubusercontent.com/monodot/openshift-nexus/master/nexus3-persistent-template.yaml
```

# Deploy Nexus 3

Deploy Sonatype Nexus 3 using one of the provided templates. If you have persistent volumes available in your cluster:
```
oc new-app nexus3-persistent
```

# Deploy Specific Version
In order to specify the Nexus version to be deployed use ```NEXUS_VERSION``` parameter:
```
oc new-app nexus3-persistent -p NEXUS_VERSION=3.5.0
```

[demorepo]: https://github.com/OpenShiftDemos/nexus

