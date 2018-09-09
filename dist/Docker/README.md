This directory contains stuff required for running or building a docker container with your custom war file. 

## run the sample from apache.org
Docker [installation](README.docker-install.md) (>=v17) is assumed to be already done.
```bash
# download
wget -O sample.war https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war

# map this .war via volumes into the container
docker run -it --rm -p 8080:8080 -v ${PWD}/sample.war:/usr/local/tomcat/webapps/sample.war tomcat:8.5.33-jre8
```
>
*NOTE*
- access _http://<ip>:8080/_ and _http://<ip>:8080/sample_ 
- tomcat starts in a quite virgin state, manager is active but not granted, etc.
- inspect the _-v_ switch and compare to your experience with the _webapp/_ directory.
- adding _/bin/bash_ the the docker-command above will take you into a shell, not starting tomcat.
> 

## get started
```bash
# clone this project
git clone git@github.com:maldex/MySimpleSampleTomcatWar.git
cd MySimpleSampleTomcatWar/

# uncompress libraries
unzip lib/libs.zip -d lib/
rm -f lib/__*.jar
```

## prepare for docker build
```
cd dist/Docker

# copy libs and configs to here
cp -Rv ../lib ./
cp -Rv ../*.xml ./

# download/aquire the actual .war file
mkdir webapps
wget -O webapps/MySimpleSampleTomcat.war https://github.com/maldex/MySimpleSampleTomcatWar/releases/download/pre-3/MySimpleSampleTomcat.war
```