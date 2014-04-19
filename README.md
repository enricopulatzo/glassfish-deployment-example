# Overview

This project demonstrates how one may use Maven to dynamically update the Glassfish version # that an application is deployed with.

The plan of attack is as follows:
- define glassfish-web.xml to include a `<version-number>` element
- the contents of that element is a token which we will replace later
- configure the build to create an exploded WAR
- configure the build to use the `replace` plugin for maven on the contents of the exploded WAR
- configure the build to package the contents of the exploded WAR as its final artifact

Once the artifact is packaged, it can merely be copied to the destination Glassfish's `autodeploy` directory. If the deployment is successful, the previously enabled version will be disabled and the new version will be enabled.
