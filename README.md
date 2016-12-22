# Sonatype Nexus on OpenShift

This repo contains OpenShift templates and scripts for deploying Sonatype Nexus
and pre-configuring Red Hat and JBoss maven repositories on Nexus


# Import Templates

In order to add Sonatype Nexus templates to OpenShift service catalog run the following commands:

```
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus2-template.yaml
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus2-persistent-emplate.yaml
```

# Deploy Nexus

Deploy Sonatype Nexus using one of the provided templates. If you have persistent
volumes available in your cluster:
```
oc new-app nexus2-persistent
```
Otherwise:
```
oc new-app nexus2
```
In order to specify the Nexus version to be deployed use ```NEXUS_VERSION``` parameter:
```
oc new-app nexus2 -p NEXUS_VERSION=2.14.2
```
