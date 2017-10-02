# Sonatype Nexus on OpenShift

This repo contains OpenShift templates and scripts for deploying Sonatype Nexus 2 an 3
and pre-configuring Red Hat and JBoss maven repositories on Nexus via post deploy hooks.
You can modify the post hook in the templates and add other Nexus repositories by using these [helper
functions](scripts/nexus-functions).

```
post:
  execNewPod:
    containerName: ${SERVICE_NAME}
    command:
      - "/bin/bash"
      - "-c"
      - "curl -o /tmp/nexus-functions -s https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/scripts/nexus-functions; source /tmp/nexus-functions; add_nexus3_redhat_repos admin admin123 http://${SERVICE_NAME}:8081"
```

# Import Templates

In order to add Sonatype Nexus templates to OpenShift service catalog run the following commands:

Sonatype Nexus 2:
```
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus2-template.yaml
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus2-persistent-template.yaml
```

Sonatype Nexus 3:
```
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus3-template.yaml
oc create -f https://raw.githubusercontent.com/OpenShiftDemos/nexus/master/nexus3-persistent-template.yaml
```

# Deploy Nexus 2

Deploy Sonatype Nexus 2 using one of the provided templates. If you have persistent volumes available in your cluster:
```
oc new-app nexus2-persistent
```
Otherwise:
```
oc new-app nexus2
```
# Deploy Nexus 3

Deploy Sonatype Nexus 3 using one of the provided templates. If you have persistent volumes available in your cluster:
```
oc new-app nexus3-persistent
```
Otherwise:
```
oc new-app nexus3
```

# Deploy Specific Version
In order to specify the Nexus version to be deployed use ```NEXUS_VERSION``` parameter:
```
oc new-app nexus2 -p NEXUS_VERSION=2.14.3
oc new-app nexus3 -p NEXUS_VERSION=3.5.2
```
