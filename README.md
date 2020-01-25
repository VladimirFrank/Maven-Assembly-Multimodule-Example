# Apache Maven Assembly plugin for multi-module

Example of creating single zip distributive from Maven multi-module project.

## Project structure
```
Parent module\
             |- plain directory with some-files (sql)
             |- java module-1 (jar)
             |- java module-2 (jar)
             \- module for distributive (final zip-package)
```

## Plugin configuration
Base build configuration described in POM file:
```
module-for-package/pom.xml
```
Required distributive content described in assembly configuration xml:
```
module-for-package/src/main/resources/package.xml
```

## Usage
Simply call Maven goals:
```
mvn clean package
```
You will see result of assembly here:
```
module-for-package/target/{name}_{version}.zip
```

## Execution steps
Maven does it something like this:
1. package module-1 and module-2;
3. read assembly plugin configuration;
4. copy module-1 and module-2 in distributive module (module-for-package);
5. copy required files (some-files) to distributive's module;
6. archive 4 and 5 steps result into zip.