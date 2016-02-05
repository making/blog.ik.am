
### Launch Redis

``` console
($ docker-machine create dev --provider virtualbox) <-- unless docker machine is set up
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

### Use Flo for Spring Cloud Data Flow

https://network.pivotal.io/products/p-flo-for-spring-cloud-data-flow


How to install is described in [this doc](http://docs.pivotal.io/spring-cloud-data-flow/index.html).

Download `flo-spring-cloud-dataflow-admin-1.0.0.M1.zip` on the same directory as `spring-cloud-dataflow-admin-local-1.0.0.M2.jar `.

``` console
$ unzip flo-spring-cloud-dataflow-admin-1.0.0.M1.zip
$ jar -u0vf spring-cloud-dataflow-admin-local-1.0.0.M2.jar lib
```

![image](https://cloud.githubusercontent.com/assets/106908/12847911/f53e749a-cc59-11e5-960d-a40134c4238f.png)


![image](https://cloud.githubusercontent.com/assets/106908/12848563/19769b4a-cc5e-11e5-99f2-206f57c021db.png)


![image](https://cloud.githubusercontent.com/assets/106908/12848588/4c098716-cc5e-11e5-83c9-856cbec0a492.png)


![image](https://cloud.githubusercontent.com/assets/106908/12848884/d17d7dd4-cc5f-11e5-9494-da678bb203b0.png)


### Deploy Admin on Cloud Foundry

Download Admin UI for Clound Foundry.

``` console
$ wget http://repo.spring.io/milestone/org/springframework/cloud/spring-cloud-dataflow-admin-cloudfoundry/1.0.0.M1/spring-cloud-dataflow-admin-cloudfoundry-1.0.0.M1.jar
($ jar -u0vf spring-cloud-dataflow-admin-cloudfoundry-1.0.0.M1.ja lib) <-- if needed
```

Create a Redis service.

``` console
$ cf create-service rediscloud 30mb scdf-redis
($ cf create-service p-redis shared-vm scdf-redis) <-- in case of PCF
```

Deploy Admin UI.

``` console
$ cf push scdf-admn -p spring-cloud-dataflow-admin-cloudfoundry-1.0.0.M1.jar --no-start
$ cf bind-service scdf-admn scdf-redis
$ cf set-env scdf-admn CLOUDFOUNDRY_API_ENDPOINT https://api.run.pivotal.io
$ cf set-env scdf-admn CLOUDFOUNDRY_ORGANIZATION {org}
$ cf set-env scdf-admn CLOUDFOUNDRY_SPACE {space}
$ cf set-env scdf-admn CLOUDFOUNDRY_DOMAIN cfapps.io
$ cf set-env scdf-admn CLOUDFOUNDRY_SERVICES scdf-redis
$ cf set-env scdf-admn CLOUDFOUNDRY_USERNAME {email}
$ cf set-env scdf-admn CLOUDFOUNDRY_PASSWORD {password}
$ cf set-env scdf-admn CLOUDFOUNDRY_SKIP_SSL_VALIDATION false
$ cf start scdf-admn
```

Access from shell

``` console
server-unknown:>admin config server http://scdf-admn.cfapps.io
Successfully targeted http://scdf-admn.cfapps.io
```

Create a stream.

```
dataflow:>stream create --name ticktock-foo --definition "time | log" --deploy
Created and deployed new stream 'ticktock-foo'
dataflow:>stream list
╔════════════╤═════════════════╤════════╗
║Stream Name │Stream Definition│ Status ║
╠════════════╪═════════════════╪════════╣
║ticktock-foo│time | log       │deployed║
╚════════════╧═════════════════╧════════╝

dataflow:>runtime modules 
╔═══════════════════════╤═══════════╤══════════════════════════════════════════════════════╗
║Module Id / Instance Id│Unit Status│            No. of Instances / Attributes             ║
╠═══════════════════════╪═══════════╪══════════════════════════════════════════════════════╣
║ticktock-foo.log       │ deployed  │                          1                           ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │        uris = ticktock-foo-log.cfapps.io             ║
║                       │           │   mem_quota = 1073741824                             ║
║                       │           │        port = 60190                                  ║
║                       │           │   usage.cpu = 0.5938522143670757                     ║
║                       │           │        name = ticktock-foo-log                       ║
║ticktock-foo-log:0     │ deployed  │        host = 192.168.8.245                          ║
║                       │           │  usage.disk = 190390272                              ║
║                       │           │  disk_quota = 1073741824                             ║
║                       │           │   fds_quota = 16384                                  ║
║                       │           │usage.memory = 517173248                              ║
║                       │           │      uptime = 42.0                                   ║
╟───────────────────────┼───────────┼──────────────────────────────────────────────────────╢
║ticktock-foo.time      │ deployed  │                          1                           ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │        uris = ticktock-foo-time.cfapps.io            ║
║                       │           │   mem_quota = 1073741824                             ║
║                       │           │        port = 61217                                  ║
║                       │           │   usage.cpu = 0.1667436182651442                     ║
║                       │           │        name = ticktock-foo-time                      ║
║ticktock-foo-time:0    │ deployed  │        host = 192.168.9.3                            ║
║                       │           │  usage.disk = 192929792                              ║
║                       │           │  disk_quota = 1073741824                             ║
║                       │           │   fds_quota = 16384                                  ║
║                       │           │usage.memory = 519127040                              ║
║                       │           │      uptime = 33.0                                   ║
╚═══════════════════════╧═══════════╧══════════════════════════════════════════════════════╝
```


``` console
$ cf apps

name                requested state   instances   memory   disk   urls   
scdf-admn           started           1/1         1G       1G     scdf-admn.cfapps.io   
ticktock-foo-log    started           1/1         1G       1G     ticktock-foo-log.cfapps.io   
ticktock-foo-time   started           1/1         1G       1G     ticktock-foo-time.cfapps.io 

$ cf logs ticktock-foo-log

2016-02-06T01:09:24.51+0900 [APP/0]      OUT 2016-02-05 16:09:24.517  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:09:24
2016-02-06T01:09:25.51+0900 [APP/0]      OUT 2016-02-05 16:09:25.518  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:09:25
2016-02-06T01:09:26.51+0900 [APP/0]      OUT 2016-02-05 16:09:26.519  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:09:26
2016-02-06T01:09:27.52+0900 [APP/0]      OUT 2016-02-05 16:09:27.520  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:09:27
2016-02-06T01:09:28.52+0900 [APP/0]      OUT 2016-02-05 16:09:28.521  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:09:28
```

Note that stream name seems to have to be unique in the same domain. Otherwise 400 error will return as follows:

``` console
dataflow:>stream create --name ticktock --definition "time | log" --deploy
Command failed org.springframework.cloud.dataflow.rest.client.DataFlowClientException: 400 Bad Request

400 Bad Request

org.springframework.cloud.dataflow.rest.client.DataFlowClientException: 400 Bad Request

    at org.springframework.cloud.dataflow.rest.client.VndErrorResponseErrorHandler.handleError(VndErrorResponseErrorHandler.java:52)
    at org.springframework.web.client.RestTemplate.handleResponse(RestTemplate.java:641)
    at org.springframework.web.client.RestTemplate.doExecute(RestTemplate.java:597)
    at org.springframework.web.client.RestTemplate.execute(RestTemplate.java:557)
    at org.springframework.web.client.RestTemplate.postForObject(RestTemplate.java:357)
    at org.springframework.cloud.dataflow.rest.client.StreamTemplate.createStream(StreamTemplate.java:79)
    at org.springframework.cloud.dataflow.shell.command.StreamCommands.createStream(StreamCommands.java:99)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:497)
    at org.springframework.util.ReflectionUtils.invokeMethod(ReflectionUtils.java:216)
    at org.springframework.shell.core.SimpleExecutionStrategy.invoke(SimpleExecutionStrategy.java:64)
    at org.springframework.shell.core.SimpleExecutionStrategy.execute(SimpleExecutionStrategy.java:57)
    at org.springframework.shell.core.AbstractShell.executeCommand(AbstractShell.java:130)
    at org.springframework.shell.core.JLineShell.promptLoop(JLineShell.java:533)
    at org.springframework.shell.core.JLineShell.run(JLineShell.java:179)
    at java.lang.Thread.run(Thread.java:745)
```

Easy to scale.

``` console
dataflow:>! cf scale ticktock-foo-time -i 2
command is:cf scale ticktock-foo-time -i 2
OK
dataflow:>runtime modules 
╔═══════════════════════╤═══════════╤══════════════════════════════════════════════════════╗
║Module Id / Instance Id│Unit Status│            No. of Instances / Attributes             ║
╠═══════════════════════╪═══════════╪══════════════════════════════════════════════════════╣
║ticktock-foo.log       │ deployed  │                          1                           ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │        uris = ticktock-foo-log.cfapps.io             ║
║                       │           │   mem_quota = 1073741824                             ║
║                       │           │        port = 60190                                  ║
║                       │           │   usage.cpu = 0.006389596662362231                   ║
║                       │           │        name = ticktock-foo-log                       ║
║ticktock-foo-log:0     │ deployed  │        host = 192.168.8.245                          ║
║                       │           │  usage.disk = 190390272                              ║
║                       │           │  disk_quota = 1073741824                             ║
║                       │           │   fds_quota = 16384                                  ║
║                       │           │usage.memory = 520814592                              ║
║                       │           │      uptime = 1039.0                                 ║
╟───────────────────────┼───────────┼──────────────────────────────────────────────────────╢
║ticktock-foo.time      │ deploying │                          2                           ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │        uris = ticktock-foo-time.cfapps.io            ║
║                       │           │   mem_quota = 1073741824                             ║
║                       │           │        port = 61217                                  ║
║                       │           │   usage.cpu = 0.0023093344768086326                  ║
║                       │           │        name = ticktock-foo-time                      ║
║ticktock-foo-time:0    │ deployed  │        host = 192.168.9.3                            ║
║                       │           │  usage.disk = 192929792                              ║
║                       │           │  disk_quota = 1073741824                             ║
║                       │           │   fds_quota = 16384                                  ║
║                       │           │usage.memory = 520687616                              ║
║                       │           │      uptime = 1030.0                                 ║
╟┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┼┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈╢
║                       │           │  usage.time = 2016-02-05 16:23:55                    ║
║                       │           │        uris = ticktock-foo-time.cfapps.io            ║
║                       │           │   mem_quota = 1073741824                             ║
║                       │           │        port = 0                                      ║
║                       │           │   usage.cpu = 0.0                                    ║
║ticktock-foo-time:1    │ deploying │        name = ticktock-foo-time                      ║
║                       │           │        host = null                                   ║
║                       │           │  usage.disk = 0                                      ║
║                       │           │  disk_quota = 1073741824                             ║
║                       │           │   fds_quota = 16384                                  ║
║                       │           │usage.memory = 0                                      ║
║                       │           │      uptime = 8.0                                    ║
╚═══════════════════════╧═══════════╧══════════════════════════════════════════════════════╝
```

``` console
$ cf logs ticktock-foo-log
2016-02-06T01:26:02.95+0900 [APP/0]      OUT 2016-02-05 16:26:02.957  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:03
2016-02-06T01:26:03.49+0900 [APP/0]      OUT 2016-02-05 16:26:03.495  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:03
2016-02-06T01:26:03.95+0900 [APP/0]      OUT 2016-02-05 16:26:03.958  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:04
2016-02-06T01:26:04.49+0900 [APP/0]      OUT 2016-02-05 16:26:04.496  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:04
2016-02-06T01:26:04.95+0900 [APP/0]      OUT 2016-02-05 16:26:04.959  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:05
2016-02-06T01:26:05.49+0900 [APP/0]      OUT 2016-02-05 16:26:05.497  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:05
2016-02-06T01:26:05.96+0900 [APP/0]      OUT 2016-02-05 16:26:05.960  INFO 15 --- [hannel-adapter1] log.sink                                 : 2016-02-05 16:26:06
2016-02-06T01:26:06.09+0900 [HEALTH/0]   OUT healthcheck passed
```
