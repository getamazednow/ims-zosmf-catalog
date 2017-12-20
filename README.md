## Setup IMS catalog z/OSMF workflow

**Overview**

With the IMS catalog  workflow you can rapidly provision catalog using the IBM® z/OS® Management Facility (z/OSMF)

The IMS catalog workflow will provision catalog to an existing IMS with these steps:
* Create the catalog database.
* Create the IMS DFSDFxxx proclib members to enable catalog.
* Establish the IMS active libraries.
* Load the catalog database.
* And optionally take an image copy of the HALDB catalog database.

**Pre-requisites**
* An SMP/E install of IMS code has been done and the IMS load libraries are available.
* Identify the z/OS system parameters
* IMS SVCs are installed on the system
* The Common Service Layer must be started.
* z/OSMF must be started. Both the angel and server z/OSMF address spaces must be started. 

**Security requirements**
* RACF read authority on SMP/E installed IMS libraries
* RACF update authority on the high level qualifiers (HLQs) you are using for the IMS instance libraries
* Authority to ADD/DELETE APF authorizations

**The IMS catalog workflows include the following files:**
* The provision.xml file
  * This is the file that provisions the catalog. You should not modify the workflow XML.
* The workflow_variables.properties file
  * The properties file contains values from the variables referenced in the provision.xml workflow.  Edit the workflow_variables.properties file specifying the system specific information for the variables in the file. 

**Installation**
* FTP the provision.xml workflow and the workflow_variables.properties file to the z/OS host USS in binary mode.
* The files need to be made visible to the z/OSMF application.  Do this by changing the access permissions of the files using the chmod command
* Examples: 
```Java
chmod 755 provision.xml
```
* Or if the file is in a folder with the name of workflows:
```Java 
chmod -R 755 workflows
```

**Common errors**
* IZUWF0105E   Workflow property file file-name is either not found or cannot be accessed

You can find the z/OSMF documentation at
https://www.ibm.com/support/knowledgecenter/search/IBM%20z%2FOS%20Management%20Facility?scope=SSLTBW_2.2.0
