[JMeter Load Testing with Concurrency : RMI Class Loader Disabled](https://stackoverflow.com/questions/48391086/jmeter-load-testing-with-concurrency-rmi-class-loader-disabled)  
こういうエラーが出たら試す

```
java.rmi.ServerExeption...java.ClassNotFoundExeption:com.Blazemeter.jmeter.threads.concurrency.ConcurrencyThreadgroup(no Security manager: RMI Class Loader disabled)
```

```taurus.yml
modules:
  jmeter:
    force-ctg: true   
    detect-plugins: true
```

[Taurus distributed load on workers with concurrency](https://stackoverflow.com/questions/69944305/taurus-distributed-load-on-workers-with-concurrency)

[Apache JMeter Distributed Testing Step-by-step](https://jmeter.apache.org/usermanual/jmeter_distributed_testing_step_by_step.html)

[Distributed JMeter - Docker](https://hub.docker.com/r/pedrocesarti/jmeter-docker)

[distributed-jmeter-docker(sample)](https://github.com/pedrocesar-ti/distributed-jmeter-docker/blob/master/local/docker-compose.yml)

[Parallel and distributed execution of multiple scenarios in taurus](https://stackoverflow.com/questions/60381423/parallel-and-distributed-execution-of-multiple-scenarios-in-taurus)

[JMeter Executor](https://gettaurus.org/docs/JMeter/)  
ramp-up, hold-forは上書きできる

