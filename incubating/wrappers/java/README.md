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