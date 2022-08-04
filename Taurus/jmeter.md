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
