# Fork of SeldonCore Repo
This fork is for the sole purpose of having control over the SeldonCore java-wrapper build which includes protobuf files that are shared between the main project and the java-wrapper. Without those protobuf files found in this repo, we can only consume SeldonCore java-wrapper with compiled protobuf. 

Unfortunately the project's compiled protobuf files were compiled with JDKxx thus creating problems when used in runtimes that can't use version xx of the JDK. 

To compile the protobufs and create an installable jar (here it is specifically versioned as 0.3.1-SNAPSHOT), follow the instructions below

For the project's readme.md see [this](README.md.orig)
# Java library for Seldon Core

A Java library to allow easy wrapping of Java models in Seldon Core.
See the docs on [how to
use](https://docs.seldon.io/projects/seldon-core/en/latest/java/README.html).

# Local Development Testing
```
cd incubating/wrappers/java
cp -r ../../../proto ./src/main/

cd src/main/proto

mv k8s k8s.src
mv tensorflow tensorflow.src

cd k8s.src
make
mv k8s.io ..

cd ../tensorflow.src
make
mv tensorflow ..

cd ../../../..
mvn protobuf:compile
mvn install
```