# iris-docker-dev-kit

**ATTENTION: THIS IS NOT AN APPLCATION!**

This is better )
This is a set of files which gives you the option to develop your InterSystems ObjectScript solution in IRIS Community Edition or IRIS Community Edition for Health on your laptop using VSCode ObjectScript extention.

## When This Works

You have a repository, which contains ObjectScript sources in CLS or XML. [Example](https://github.com/intersystems-ru/Cache-translate)
And you want to run, edit, compile, debug code and probably commit, push ObjectScript to your repository back.

This repository is for you in this case!

## Installation

Download the [latest release zip](https://github.com/evshvarov/iris-docker-dev-kit/releases/tag/0.1) and unpack files in your repository folder.
Check the line 16 in Dockerfile, which looks like this:

```
COPY src src
```

This line copies source files from /src folder in your repository to /src subfolder in Docker container's to import it then into IRIS. Change the first src to the name of the folder with ObjectScript you want to be imported to IRIS. If you have several files or folders repeat this COPY command for each resource accordingly.
That's it.

## How to Run the Application

Open InterSystems IRIS terminal:

```
$ docker-compose exec iris iris session iris
USER>zn "IRISAPP"
IRISAPP>do ##class(Contest.ObjectScript).TheUniverseQuestion()
42
```
## How to start coding
This repository is ready to code in VSCode with ObjectScript plugin.
Install [VSCode](https://code.visualstudio.com/), [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) and [ObjectScript](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript) plugins and open the folder in VSCode.

Right-click on **docker-compose.yml** file and click Compose Restart

Once docker will finish starting procedure and show:

```
Creating objectscript-contest-template_iris_1 ... done
```

Click on the ObjectScript status bar and select Refresh connection in the menu.
Wait for VSCode to make connection and show something like "localhost:32778[IRISAPP] - Connected"

You can start coding after that. Open **ObjectScript.cls** in VSCode, make changes and save - the class will be compiled by IRIS on 'Save'.

## Happy coding!