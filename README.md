# SUIT 

SUIT (Science User Interface and Tools) repository contains a sample application built with [Firefly] (https://github.com/lsst/firefly)

## Requirements

 - Clone [Firefly] (https://github.com/lsst/firefly) reository
 - Follow instructions at [Firefly setup] (https://github.com/lsst/firefly#setup) to install tomcat, gradle, java 1.8 and node
 - Build lsstviewer using command: 

`gradle :lsstviewer:war`

 - Start tomcat (Ubuntu 14.04) 
 
`/usr/share/apache-tomcat-7.0.65/bin$ ./startup.sh` 
 
 - Deploy lsstviewer.war to tomcat (Ubuntu 14.04)
 
`cp suit/build/libs/lsstviewer.war /usr/share/apache-tomcat-7.0.65/webapps/`
 
From a web browser open the app at this URL: 

`localhost:8080/lsstviewer/app.html`

## How to setup a search form

The search forms are specified by XML files, see examples at `suit/lsstviewer/config/configurable`

## How to write a search processor

The `DataSource` element in the XML has the `searchProcId` attribute, it tells Firefly which search processor to use.

As the result of the processing, the search processor must create a CSV file e.g [TestPythonLauncher.py] (https://github.com/lsst-sqre/suit/blob/master/src/lsstviewer/python/TestPythonLauncher.py)

## Changing the `app.pro` configuration file

You must set the search path for fits files here, e.g:

`visualize.fits.search.path=/home/<user>/lsst`

and include the path for the search processor, e.g:

`python.exe=/bin/python /home/<user>/lsst/test.py`




