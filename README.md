## Setup IMS catalog

**Overview**

With the IMS catalog workflow you can rapidly provision the catalog using the IBM® z/OS® Management Facility (z/OSMF)

The IMS catalog workflow will provision the catalog to an existing IMS with these steps:
* Create the catalog database.
* Create the IMS DFSDFxxx proclib members to enable IMS catalog.
* Establish the IMS active libraries.
* Load the catalog database.

The workflow will also optionally take an image copy of the HALDB catalog database.

**Pre-requisites**
* An SMP/E installation of IMS is done and the IMS load libraries are available.
* Identify the z/OS system parameters
* IMS SVC modules are installed on the system
* The Common Service Layer must be started.
* z/OSMF must be started. Both the angel and server z/OSMF address spaces must be started. 

**Security requirements**  
To run the workflow, you need the following authority:
* RACF read authority on SMP/E installed IMS libraries
* RACF update authority on the high level qualifiers (HLQs) you are using for the IMS instance libraries
* Authority to ADD/DELETE APF authorizations

**Package structure**  
The repository includes the following files:
* setupCatalog.xml
  * This is the file that provisions the catalog. You should not modify the workflow XML.
* workflow_variables.properties
  * This properties file contains values from the variables referenced in the setupCatalog.xml workflow. Edit the workflow_variables.properties file to specify the system specific information for the variables in the file. 

**Installation**  
* FTP the setupCatalog.xml workflow and the workflow_variables.properties file to the z/OS host USS in binary mode.
* The files need to be made visible to the z/OSMF application.  Do this by changing the access permissions of the files using the chmod command
* Example chmod commands: 
```Java
chmod 755 setupCatalog.xml
```
* Or if the file is in a folder with the name of workflows:
```Java 
chmod -R 755 workflows
```

**Common errors**
* IZUWF0105E   Workflow property file file-name is either not found or cannot be accessed
  * Typically this error comes from the file not existing at the path given, or the file exists, and chmod needs to be done on this file.


**z/OSMF documentation**

Visit the IBM Knowledge Center for more information on [IBM z/OS Management Facility](https://www.ibm.com/support/knowledgecenter/search/IBM%20z%2FOS%20Management%20Facility?scope=SSLTBW_2.2.0)
