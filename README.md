# Command Line Tool Wrapping SHACL API provided by TopQuadrant

**An open source implementation which wraps the SHACL API provided by Holger Knublauch (holger@topquadrant.com).**

The submodule TopQuandrantShacl is linked to https://github.com/TopQuadrant/shacl.

The subfolder shacl-cl contains the wrapper using the API provided by TopQuadrant.

## Building

```bash
git submodule update --init
cd TopQuandrantShacl
mvn install
cd..
cd shacl-cl
mvn package
```

This generates an executable jar file `target/shacl-validator-0.0.2-jar-with-dependencies.jar`.

## Usage

Here is an example how to use the SHACL validator:

I assume that you are just outside the `shacl-cl` directory.

```bash
# download some DCAT-AP.de conformant RDF document
mkdir data
wget -O data/catalog.ttl https://transparenz.schleswig-holstein.de/catalog.ttl

# get the DCAT-AP.de SHACL validation files
git clone https://github.com/GovDataOfficial/DCAT-AP.de-SHACL-Validation.git

# start the validation
java -jar shacl-cl/shacl-cl/target/shacl-validator-0.0.2-jar-with-dependencies.jar -s DCAT-AP.de-SHACL-Validation/validator/resources/v1.0.2/shapes -p data/
```

