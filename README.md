# skeleton-proxy
The skeleton-proxy is an example proxy application template for building an HTTP proxy in Mule. The proxy contains automated
API configuration for Anypoint API Manager 2.x. Automated API configuration registers the proxy into the NP1, NP2, NP3 and PROD environments. In addition,
the configuration property files for each environment are updated to include the API registration information. The proxy application
can also be deployed to an environment.

Deployment server configuration information is stored in the Maven settings.xml file.
Deployment is executed with the deploy goal (it uses the mule-maven-plugin).
API configuration is executed with ApiConfigTool (using the exec-maven-plugin).

## Prerequisites for Using Template
1. Java 1.8 JDK needs to be installed.
2. Maven 3.3.9 needs to be installed and configured for use.
3. The sample-settings.xml file needs to be taken from the project, updated to have appropriate user credentials, Anypoint configuration values (like environment, server and business group names).
4. The timerInterceptor project needs to be download and built (mvn clean install).
5. The ApiConfigTool project needs to be download and built (mvn clean install).

## Using the Template


1. Import the template project (as a Maven project) into Anypoint Studio.
2. Do a file search and locate all the occurrences of the string "skeleton" and replace them with your API's name.
3. Update the configuration files in the src/main/resources directory to have the correct implementation values.
4. Update the *-policies.json files to have the correct policy definitions.
5. Save all the changes.
6. Configure the API with the mvn command.
7. Test the API in Studio (use mule.env=local and mule.key=Mulesoft12345678).
8. Save any changes to GitHub.
9. Deploy the API to NP1 using mvn command.


## Configure APIs

Configuring API's only needs to be run once, the API Manager will be updated for all four environments (NP1..NP3 and PROD). The configuration property files for each environment will be updated with the API Manager assigned values. To configure the APIs, use this command:

```
mvn clean install -Pconfig-api
```

## Deploy the API to an environment

The deployment will build the proxy from the project source code and push the deployable archive to the specified environment using the
Anypoint Runtime Manager. Note that the API should be configured prior to deploying. Use the following command to deploy to the NP1
environment:

```
mvn clean install deploy -Denv=np1
```
## Configure API and Deploy

Use this command to configure the API and deploy:

```
mvn clean install deploy -Denv=np1 -Pconfig-api
```


