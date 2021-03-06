# Access control extension
## Extend the data model for Access control.

[Example: Extend the data model for Access control from Community](https://community.backbase.com/documentation/DBS/latest/access_control_extend_data_model)

## Description
This example shows you how to modify the default behavior of the Access control service. 
This modification allows to extend the data model for Access control using additions.

## How to use
To use your service extension, you include the property file to the CLASSPATH and define 
`spring.config.additional-location` environment variable when the service is started.

[When you run a service as a bootable jar](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#executable-jar-property-launcher-features), 
you can configure custom config location. For example: 

    java -Dspring.config.additional-location=C:\Backbase\access-control-data-extension\src\main\resources\apiExtensionAccessControl.yml -jar access-control.jar
    
If you are not running the Service as a war, use the mechanism available in your application server.

### Docker
As an example we include a [Dockerfile](Dockerfile) showing how we could extend our Backbase Docker images
with additional configuration we just created.

    mvn package -Pdocker

After the build finishes we will have a Docker image with our additional configuration inside.
Set the following environment variable when running the docker image.

    SPRING_CONFIG_ADDITIONAL-LOCATION: "classpath:/apiExtensionAccessControl.yml"
