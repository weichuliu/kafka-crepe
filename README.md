# kafka-crepe
A Kafka Configuration Grepping Tool

The `kafka-crepe` is a commandline tool to search Kafka related configurations (`broker`, `producer`, `consumer`, etc). `crepe` means **C**onfiguration **R**egular **E**xpression (matching and) **P**rint **E**ureka!

Ever tried to search the Kafka documentation page for a certain configuration and feel your eyes are bleeding? Try `kafka-crepe`.

### Usage

```
$ ./kafka-crepe.py -h
usage: kafka-crepe.py [-h] [-d DOC] [-f FORMAT] keyword
```

`kafka-crepe` searches configurations that match `keyword` and print it to terminal.

`-d` specifies which configuration document do you want to search. For instance, `-d producer` will search from producer configurations. By default it is `-d kafka`, which is broker configuration.

`-f` sets the output format. `-f name` will print only configuration name, and `-f details` will print additional information, such as description, default, etc.

### How Does This Work

Configuration documents are stored in the submodule `kafka-site`. It contains documents for all versions.

`kafka-site/[ver]/generated` stores the auto generated configurations (`kafka_config`, `producer_config`, etc).

`kafka-docs` is a symlink that points to `kafka-site/[latest version]/generated`. `kafka-crepe` uses the link to find documents to search.

### Download Submodule

`kafka-crepe` relies on submodule `kafka-site` so it has to be pulled down to local.

When git clone kafka-crepe, clone with `--recursive`.

### Environment

`kafka-crepe` runs with Python3, depends on `BeautifulSoup 4` and `Termcolor`. A proper `requirements.txt` is on TODO list.
