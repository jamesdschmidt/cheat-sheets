# virtualenv Cheat Sheet

This cheat sheet is for those who like spam (https://www.youtube.com/watch?v=zLih-WQwBSc).

## Create Environment
```
$ virtualenv --python python2 my-new-environment
```

## Activate Environment
```
$ activate my-new-environment/bin/activate
```

## Deactivate Environment
```
(my-new-environment)$ deactivate
```

## List Environments
```
$ lsvirutualenv
```

## Remove an Environment
```
(my-new-environment)$ deactivate
$ rm -r /path/to/my-new-environment
```

For more see https://virtualenv.pypa.io/en/latest/userguide/#usage
