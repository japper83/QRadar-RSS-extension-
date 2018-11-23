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

```
qradar_app_creator create -w <path to myapp>
```

example: 

```
qradar_app_creator create -w ~/QradarApps/com.me.myApp.1.0.0
```


#### Python Modules

src_dps pip 
pip2tgz


#### Persistent storage 

### QRadar SDK Run an App Locally

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
```
qradar_app_creator package -w <path to myapp> -p <name of the zip file>
```
Example:
```
qradar_app_creator package -w ~/QradarApps/com.me.myApp.1.0.0/ -p com.me.myApp.1.0.0.zip
```

### QRadar SDK Deploy an App
```
qradar_app_creator deploy -q <QRadar console IP address> -u <QRadar user> -p com.mycompany.myapp.zip
```
Example:
```
qradar_app_creator deploy -q 192.168.1.100 -u admin -p com.me.myApp.1.0.0.zip
```

### QRadar SDK Check app status
```
qradar_app_creator status -q <QRadar console IP address> -u <QRadar user> -a <app ID>
```
Example:
```
qradar_app_creator status -q 192.168.1.100 -u admin -a 1051
```

### QRadar SDK Delete an app
```
qradar_app_creator delete -q <QRadar console IP address> -u <QRadar user> -a <app ID>
```
Example:
```
qradar_app_creator delete -q 192.168.1.100  -u admin -a 1051
```
### QRadar SDK logs



## QRadar extension


## Built With
feedparser
rfeed
* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds



