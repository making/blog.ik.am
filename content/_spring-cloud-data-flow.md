
### Launch Redis

``` console
($ docker-machine create dev --provider virtualbox)
$ docker run -d --name redis -p 6379:6379 redis
$ docker-machine ssh dev -f -N -L 6379:localhost:6379
```

### Setup Admin UI (Local)

``` console
$ wget http://repo.spring.io/milestone/org/springframework/cloud/spring-cloud-dataflow-admin-local/1.0.0.M2/spring-cloud-dataflow-admin-local-1.0.0.M2.jar
$ java -jar spring-cloud-dataflow-admin-local-1.0.0.M2.jar 
```

### Run Shell

``` console
$ wget http://repo.spring.io/milestone/org/springframework/cloud/spring-cloud-dataflow-shell/1.0.0.M2/spring-cloud-dataflow-shell-1.0.0.M2.jar
$ java -jar spring-cloud-dataflow-shell-1.0.0.M2.jar 
```

``` console
  ____                              ____ _                __
 / ___| _ __  _ __(_)_ __   __ _   / ___| | ___  _   _  __| |
 \___ \| '_ \| '__| | '_ \ / _` | | |   | |/ _ \| | | |/ _` |
  ___) | |_) | |  | | | | | (_| | | |___| | (_) | |_| | (_| |
 |____/| .__/|_|  |_|_| |_|\__, |  \____|_|\___/ \__,_|\__,_|
  ____ |_|    _          __|___/                 __________
 |  _ \  __ _| |_ __ _  |  ___| | _____      __  \ \ \ \ \ \
 | | | |/ _` | __/ _` | | |_  | |/ _ \ \ /\ / /   \ \ \ \ \ \
 | |_| | (_| | || (_| | |  _| | | (_) \ V  V /    / / / / / /
 |____/ \__,_|\__\__,_| |_|   |_|\___/ \_/\_/    /_/_/_/_/_/

1.0.0.M2

Welcome to the Spring Cloud Data Flow shell. For assistance hit TAB or type "help".

dataflow:>stream create --name ticktock --definition "time | log"
Created new stream 'ticktock'
dataflow:>stream list
╔═══════════╤═════════════════╤══════════╗
║Stream Name│Stream Definition│  Status  ║
╠═══════════╪═════════════════╪══════════╣
║ticktock   │time | log       │undeployed║
╚═══════════╧═════════════════╧══════════╝

dataflow:>stream deploy --name ticktock
Deployed stream 'ticktock'
dataflow:>stream list
╔═══════════╤═════════════════╤════════╗
║Stream Name│Stream Definition│ Status ║
╠═══════════╪═════════════════╪════════╣
║ticktock   │time | log       │deployed║
╚═══════════╧═════════════════╧════════╝
dataflow:>runtime modules 
╔═══════════════════════╤═══════════╤════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╗
║Module Id / Instance Id│Unit Status│                                                   No. of Instances / Attributes                                                    ║
╠═══════════════════════╪═══════════╪════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╣
║ticktock.log           │ deployed  │                                                                 1                                                                  ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │working.dir = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.log              ║
║ticktock.log-0         │ deployed  │     stdout = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.log/stdout_0.log ║
║                       │           │     stderr = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.log/stderr_0.log ║
║                       │           │        url = http://192.168.16.82:10417                                                                                            ║
╟───────────────────────┼───────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╢
║ticktock.time          │ deployed  │                                                                 1                                                                  ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │working.dir = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.time             ║
║ticktock.time-0        │ deployed  │     stdout = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.time/stdout_0.log║
║                       │           │     stderr = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.time/stderr_0.log║
║                       │           │        url = http://192.168.16.82:23869                                                                                            ║
╚═══════════════════════╧═══════════╧════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╝
```

``` console
2016-02-05 17:09:26.732  INFO 5031 --- [nio-9393-exec-4] o.s.c.d.a.s.l.OutOfProcessModuleDeployer : deploying module org.springframework.cloud.stream.module:log-sink:jar:exec:1.0.0.M2 instance 0
   Logs will be in /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.log
2016-02-05 17:09:26.744  INFO 5031 --- [nio-9393-exec-4] o.s.c.d.a.s.l.OutOfProcessModuleDeployer : deploying module org.springframework.cloud.stream.module:time-source:jar:exec:1.0.0.M2 instance 0
   Logs will be in /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.time
```


``` console
$ tail -f /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4275479898095958756/ticktock.log/stdout_0.log
2016-02-05 17:18:20.239  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:20
2016-02-05 17:18:21.245  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:21
2016-02-05 17:18:22.248  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:22
2016-02-05 17:18:23.254  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:23
2016-02-05 17:18:24.259  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:24
2016-02-05 17:18:25.263  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:25
2016-02-05 17:18:26.269  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:26
2016-02-05 17:18:27.273  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:27
2016-02-05 17:18:28.278  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:28
2016-02-05 17:18:29.283  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:29
2016-02-05 17:18:30.289  INFO 5243 --- [hannel-adapter1] log.sink                                 : 2016-02-05 17:18:30
```

``` console
$ jps
5043 jar
5555 Jps
5031 jar
5243 spring-cloud-stream-module-launcher5520082976132501233.jar
5244 spring-cloud-stream-module-launcher5520082976132501233.jar
```

[http://localhost:9393/admin-ui/index.html#/streams/definitions](http://localhost:9393/admin-ui/index.html#/streams/definitions)

![image](https://cloud.githubusercontent.com/assets/106908/12841193/6104542e-cc2d-11e5-8745-5288b6e705bf.png)

[http://localhost:9393/admin-ui/index.html#/containers/containers](http://localhost:9393/admin-ui/index.html#/containers/containers)

![image](https://cloud.githubusercontent.com/assets/106908/12841206/757e2132-cc2d-11e5-8762-e60dfd244fcd.png)

![image](https://cloud.githubusercontent.com/assets/106908/12841226/93e0dba6-cc2d-11e5-8f99-dac5847a6f49.png)


``` console
dataflow:>stream destroy ticktock
Destroyed stream 'ticktock'
```

### Use Modules

``` console
dataflow:>module list
╔══════════════╤════════════════╤═══════════════════╤════╗
║    source    │   processor    │       sink        │task║
╠══════════════╪════════════════╪═══════════════════╪════╣
║file          │filter          │cassandra          │    ║
║ftp           │groovy-filter   │counter            │    ║
║http          │groovy-transform│field-value-counter│    ║
║load-generator│httpclient      │file               │    ║
║sftp          │noop            │ftp                │    ║
║tcp           │pmml            │gemfire            │    ║
║time          │splitter        │hdfs               │    ║
║twitterstream │transform       │jdbc               │    ║
║              │                │log                │    ║
║              │                │redis              │    ║
║              │                │tcp                │    ║
║              │                │throughput         │    ║
║              │                │websocket          │    ║
╚══════════════╧════════════════╧═══════════════════╧════╝
```

Let's use `http` as source and `file` as sink!

``` console
dataflow:>stream create --name demo --definition "http --server.port=9000 | file --directory=/tmp/out" --deploy
Created and deployed new stream 'demo'
dataflow:>runtime modules 
╔═══════════════════════╤═══════════╤════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╗
║Module Id / Instance Id│Unit Status│                                                 No. of Instances / Attributes                                                  ║
╠═══════════════════════╪═══════════╪════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╣
║demo.file              │ deployed  │                                                               1                                                                ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │working.dir = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.file             ║
║demo.file-0            │ deployed  │     stdout = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.file/stdout_0.log║
║                       │           │     stderr = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.file/stderr_0.log║
║                       │           │        url = http://192.168.16.82:65385                                                                                        ║
╟───────────────────────┼───────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╢
║demo.http              │ deployed  │                                                               1                                                                ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │working.dir = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.http             ║
║demo.http-0            │ deployed  │     stdout = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.http/stdout_0.log║
║                       │           │     stderr = /var/folders/15/fww24j3d7pg9sz196cxv_6xm4nvlh8/T/spring-cloud-data-flow-4734634153643730467/demo.http/stderr_0.log║
║                       │           │        url = http://192.168.16.82:9000                                                                                         ║
╚═══════════════════════╧═══════════╧════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════╝
```

Access 

``` console
$ curl -X POST -d "Hello World1" -H "Content-Type: text/plain" localhost:9000
$ curl -X POST -d "Hello World2" -H "Content-Type: text/plain" localhost:9000
$ curl -X POST -d "Hello World3" -H "Content-Type: text/plain" localhost:9000
```

``` console
$ tail -f /tmp/out/file-sink 
Hello World1
Hello World2
Hello World3
```


``` console
dataflow:>stream destroy demo
Destroyed stream 'demo'
dataflow:>stream create --name demo --definition "http --server.port=9000 | transform --expression=payload.toUpperCase() | file --directory=/tmp/out" --deploy
Created and deployed new stream 'demo'
```

``` console
$ curl -X POST -d "Hello World1" -H "Content-Type: text/plain" localhost:9000
$ curl -X POST -d "Hello World2" -H "Content-Type: text/plain" localhost:9000
$ curl -X POST -d "Hello World3" -H "Content-Type: text/plain" localhost:9000
```

``` console
$ tail -f /tmp/out/file-sink 
HELLO WORLD1
HELLO WORLD2
HELLO WORLD3
```
