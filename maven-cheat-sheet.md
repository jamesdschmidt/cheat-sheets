# Maven Cheat Sheet

## Compiling

Delete target directory
```shell
% mvn clean
```

Compile the source
```shell
% mvn compile
```

Create the package
```shell
% mvn package
```

Create the package and install locally
```shell
% mvn clean install
```

Create the package and install locally
```shell
% mvn verify
```

## Testing

Run tests
```shell
% mvn test
```

Skip testing
```shell
% mvn verify -DskipTests=true
```

Skip compiling the tests
```shell
% mvn verify -Dmaven.test.skip=true
```

## Dependencies

List dependencies
```shell
% mvn dependency:list
```

List dependency tree
```shell
% mvn dependency:tree
```

Search for dependency
```shell
% mvn dependency:list | grep log4j
```
