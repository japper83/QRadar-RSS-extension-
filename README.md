# QRadar RSS extension

One Paragraph of project description goes here

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

* [QRadar SDK download](https://exchange.xforce.ibmcloud.com/hub/extension/517ff786d70b6dfa39dde485af6cbc8b)- An IBM-ID is required for the download

* Python 2.7.9 or later (Python 3 is not supported )


### QRadar SDK installing
Deploy an App



A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

Example

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

### QRadar SDK Create an App
To create a virtual development environment for the QRadar app run the following command:

```
qradar_app_creator create -w <path to myapp>
```

example: 

```
qradar_app_creator create -w ~/QradarApps/com.me.myApp.1.0.0
```

The QRadar SDK will create the following files and folders:

* app – contains source files for the app
* manifest.json – JSON manifest file that describes the app
* qradar_appfw_venv – Python virtual environment for running your app locally
* run.py – default Python script for running your app locally


#### Python Modules
You can install Python Modules in the QRadar SDK by using the Python virtual environment. The example below will install 
Feedparser in the QRadar SDK.

```
 ~/QradarApps/com.me.myApp.1.0.0/qradar_appfw_venv/bin/pip install feedparser
```
Feedparser will now be avalable for the Python virtual environment. The Python Modules must be present in the src_deps folder if the app is deployed on QRadar. Use pip2tgz to convert the python module in a tar.gz file. 

Example:
```
pip install pip2pi 
pip2tgz ~/QradarApps/com.me.myApp.1.0.0/src_deps/pip feedparser
```
More info on:
* [QRadar SDK src_deps webpage](https://www.ibm.com/support/knowledgecenter/en/SS42VS_7.2.8/com.ibm.appfw.doc/c_appframework_dependencies.html)
#### Persistent storage 
The QRadar app is deployed within containers on the QRadar Server, the storage is not persistent in the containers. You can use the store folder in the QRadar app for persistent storage. Every file or folder will remain intact after a reboot of the application or server. 
### QRadar SDK Run an App Locally
The QRadar SDK app can be tested Locally by running the app with the following command: 

```
qradar_app_creator run -w <path to myapp>
```

Example:
```
qradar_app_creator run -w ~/QradarApps/com.me.myApp.1.0.0/
```

The app will be running on
```
0.0.0.0:5000
```
### QRadar SDK Package an App
If the QRadar app is fully tested it can be deployed on a QRadar Server. First the QRadar app must be packaged with the following command: 
```
qradar_app_creator package -w <path to myapp> -p <name of the zip file>
```
Example:
```
qradar_app_creator package -w ~/QradarApps/com.me.myApp.1.0.0/ -p com.me.myApp.1.0.0.zip
```

### QRadar SDK Deploy an App
The QRadar SDK app package can now be deployed on the QRadar Server with the command below. An user with admin privileges is required for the deployment.    
```
qradar_app_creator deploy -q <QRadar console IP address> -u <QRadar user> -p com.mycompany.myapp.zip
```
Example:
```
qradar_app_creator deploy -q 192.168.1.100 -u admin -p com.me.myApp.1.0.0.zip
```

### QRadar SDK Check app status
During the creation of the app, QRadar will assign an unique app id to the application. To check the status of the application use following command using the new app id:  
```
qradar_app_creator status -q <QRadar console IP address> -u <QRadar user> -a <app ID>
```
Example:
```
qradar_app_creator status -q 192.168.1.100 -u admin -a 1051
```

### QRadar SDK Delete an app
The app can be deleted using the following command: 
```
qradar_app_creator delete -q <QRadar console IP address> -u <QRadar user> -a <app ID>
```
Example:
```
qradar_app_creator delete -q 192.168.1.100  -u admin -a 1051
```
### QRadar SDK logs
You can track the creation of the app by connecting to the QRadar server with SSH. In the console run the below command to get a list of QRadar apps running in containers   

```
sudo /opt/qradar/support/qapp_utils_730.py ps
```

Connect to the container with the corresponding app id.  
```
sudo /opt/qradar/support/qapp_utils_730.py connect <app id>
```  

Example:
```  
sudo /opt/qradar/support/qapp_utils_730.py connect 1051
```

After connection run the below command to monitor the creation of the app. If something is wrong with the creation the below command will display the error. 
```
tail -f /store/log/startup.log
```
## QRadar extension
After fully testing the deployed app, the app can be converted in an extension for deploying to the production server. connect to the QRadar server with SSH. Run the command below to create the extension.  
```
/opt/qradar/bin/contentManagement.pl --action export --content-type 100 --id <app id> 
```

Example:
```
/opt/qradar/bin/contentManagement.pl --action export --content-type 100 --id 1051
```
The extension will be created in /opt/qradar/bin with the following naming format:
```
installed_application-ContentExport-YYYYMMDDhhmmss.zip
```
Example
```
installed_application-ContentExport-20160911141607.zip
```
The extension can now be deployed on the Qradar production server with the Qradar extension manager 

## QRadar information

More information can be found with the links below:
* [QRadar SDK Create,Run,Package,Deploy](https://developer.ibm.com/qradar/whats-new/)

* [QRadar SDK src_deps webpage](https://www.ibm.com/support/knowledgecenter/en/SS42VS_7.2.8/com.ibm.appfw.doc/c_appframework_dependencies.html)

* [QRadar SDK Create extension](https://www.ibm.com/support/knowledgecenter/en/SS42VS_7.3.0/com.ibm.appfw.doc/t_appframework_createExt.html)

