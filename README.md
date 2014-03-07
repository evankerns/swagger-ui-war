## swagger-ui-war

At time of writing, the instructions for including [https://github.com/wordnik/swagger-ui](https://github.com/wordnik/swagger-ui "swagger-ui") in a web application are as follows:

> You can use the swagger-ui code AS-IS! No need to build or recompile--just clone this repo and use the pre-built files in the dist folder. If you like swagger-ui as-is, stop here.

All well and good, but that means maintaining changes from upstream swagger-ui. If we have multiple applications using swagger-ui, that means we may have multiple different versions of swagger-ui deployed at any one time.

The purpose of this module is to provide a Maven war module that TASC web applications can include using the Maven war overlay method.

### Install

1. Clone this repo
2. mvn deploy

### Using in other applications

1. Add this war as a runtime dependency to your pom:
 
    <dependency>
        <groupId>com.tasconline.web</groupId>
        <artifactId>swagger-ui-war</artifactId>
		<scope>runtime</scope>
		<type>war</type>
	</dependency>
    
2. Add the overlay to your build/plugins. Set the *targetPath* option to whichever subdirectory you want to serve the content from:

     <plugin>
		<groupId>org.apache.maven.plugins</groupId>
		<artifactId>maven-war-plugin</artifactId>
		<configuration>
			<overlays>
        		<overlay>
        			<groupId>com.tasconline.web</groupId>
            		<artifactId>swagger-ui-war</artifactId>
              		<targetPath>docs</targetPath>
            	</overlay>
            </overlays>
		</configuration>
	</plugin>

And you are done!

### TODO

- Eliminate this project altogether. Skip the git clone; submit a pull request to upstream swagger-ui that uses npm grunt modules to build a war and deploy to Maven repositories.

