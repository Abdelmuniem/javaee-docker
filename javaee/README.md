# Basic Java EE CRUD Application
This is the basic Java EE 8 application used throughout the Docker and Kubertenes demos. It is a simple CRUD application. It uses Maven and Java EE 8 (JAX-RS, EJB, CDI, JPA, JSF, Bean Validation).

We use Eclipse but you can use any Maven capable IDE such as NetBeans. We use WebSphere Liberty but you should be able to use any Java EE 8 compatiple application server such as WildFly or Payara. We use Postgres but you can use any relational database such as MySQL.

## Setup

- Install JDK 8+.
- Install the Eclipse IDE for Java EE Developers from [here](https://www.eclipse.org/downloads/packages/).
- Install WebSphere Liberty in Eclipse by following the instructions [here](https://developer.ibm.com/wasdev/downloads/liberty-profile-using-eclipse/). Make sure to install WebSphere Liberty with full Java EE 8 (you can automatically download right from the IDE).
- Install Docker for your OS.
- Download this repository somewhere in your file system (easiest way might be to download as a zip and extract).

## Database Creation
The first step to getting the application running is getting the database up. The simplest way to actually do this is through Docker. Please follow the instructions [here](javaee-cafe-demo/database/README.md) to get the database running.

## Running the Application
The next step is to get the application up and running. Follow the steps below to do so.
* Start Eclipse.
* Get the javaee-cafe application into the IDE. In order to do that, go to File -> Import -> Maven -> Existing Maven Projects. Then browse to where you have this repository code in your file system and select javaee/javaee-cafe. Accept the rest of the defaults and finish.

Datasource is configured on WEB-INF/web.xml file, by default with next properties:

**Server:** localhost
**Port:** 5432
**Database-name:** postgres
**User:** postgres
**Password:** 123

The database can be run with next command

```
docker run -it --rm  --name JavaEEDemoDB -v pgdata:/var/lib/postgresql/data -p 5432:5432 -d postgres
```

## Build

Clone this repository and build the examples using:

```
mvn package
```

## Content

This application is composed by:

- **A RESTFul service*:** protocol://hostname:port/javaee-cafe/webapi/cafeRS

	- **_GET by Id_**: protocol://hostname:port/javaee-cafe/webapi/cafeRS/{id} 
	- **_GET all_**: protocol://hostname:port/javaee-cafe/webapi/cafeRS/all 
	- **_POST_** to add a new element
	- **_DELETE_** to delete an element


- **A Java Server Faces Client:** protocol://hostname:port/javaee-cafe/index.xhtml
