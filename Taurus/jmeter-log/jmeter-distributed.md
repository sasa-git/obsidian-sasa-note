[Apache JMeter 4.0 を使用した Docker 分散テスト](https://www.blazemeter.com/blog/jmeter-distributed-testing-with-docker)

この記事の例は、Apache JMeter 3.3 に基づいています。最近、JMeter の新しいメジャー バージョンであるバージョン4.0がリリースされ、分散テスト設定に重要な変更が加えられました。クライアントとサーバー間のデフォルトの通信は、安全なRMIチャネルに基づいており、キーストアが必要です。

→解決方法
各インスタンスに「-Jserver.rmi.ssl.disable=true」を追加してセキュア RMI を無効にします。

```yml
execution:
- distributed:
  - loadtest-cluster-slave-1:60000
  - loadtest-cluster-slave-2:60000
  - loadtest-cluster-slave-3:60000
  scenario: some_scenario
  hold-for: 1m

scenarios:
  some_scenario:
    requests:
      - https://google.com


modules:
  jmeter:
    properties:
      server.rmi.ssl.disable: true

settings:
  artifacts-dir: /var/taurus/logs
  check-updates: false
```

```yml
execution:
- distributed:
  - loadtest-cluster-slave-1:60000
  - loadtest-cluster-slave-2:60000
  - loadtest-cluster-slave-3:60000
  scenario: some_scenario
  hold-for: 1m

scenarios:
  some_scenario:
    requests:
      - https://google.com


modules:
  jmeter:
    properties:
      server.rmi.ssl.disable: true
      client.rmi.localport: 7000
      my-hostname: master
    force-ctg: true
    detect-plugins: true

settings:
  artifacts-dir: /var/taurus/logs
  check-updates: false
```

`/root/.bzt/jmeter-taurus/5.4.3/bin/jmeter -n -t logs/modified_requests.jmx -j jmeter.log -R loadtest-cluster-slave-1:60000 -Dclient.rmi.localport=7000 -Djava.rmi.server.hostname=loadtest-cluster-slave-1 -Dserver.rmi.ssl.disable=true`

`jmeter -n -t scenario.jmx -j jmeter.log -R loadtest-cluster-slave-1:60000 -Dclient.rmi.localport=7000 -Djava.rmi.server.hostname=loadtest-cluster-slave-1:61000 -Dserver.rmi.ssl.disable=true`

```yml
execution:
- distributed:
  - loadtest-cluster-slave-1:60000
  - loadtest-cluster-slave-2:60000
  - loadtest-cluster-slave-3:60000
  scenario: some_scenario
  # hold-for: 1m

scenarios:
  some_scenario:
    script: my-test.jmx
    # requests:
    #   - https://google.com


modules:
  jmeter:
    properties:
      server.rmi.ssl.disable: true
      client.rmi.localport: 7000
    force-ctg: true
    detect-plugins: true

settings:
  artifacts-dir: /var/taurus/logs
  check-updates: false

~reporting:
- module: final-stats # テスト後の要約統計量を提供します
  summary: true  # 全体的なサンプル数と失敗の割合
  percentiles: true  # 平均時間と割合を表示
  summary-labels: true # サンプルラベル、ステータス、完了率、平均時間、エラーのリストを提供
  failed-labels: false  # 失敗したサンプルラベルのリストを提供
  test-duration: true  # テスト期間を提供します
  dump-csv: /var/taurus/logs/perf_result_csv.csv
  dump-xml: /var/taurus/logs/perf_result_xml.xml
```

```xml
<?xml version='1.0' encoding='UTF-8'?>
<jmeterTestPlan>
  <hashTree>
    <TestPlan guiclass="TestPlanGui" testname="BZT Generated Test Plan" testclass="TestPlan" enabled="true">
      <elementProp name="TestPlan.user_defined_variables" elementType="Arguments" guiclass="ArgumentsPanel" testclass="Arguments"/>
    <boolProp name="TestPlan.functional_mode">false</boolProp></TestPlan>
    <hashTree>
      <com.blazemeter.jmeter.threads.concurrency.ConcurrencyThreadGroup guiclass="com.blazemeter.jmeter.threads.concurrency.ConcurrencyThreadGroupGui" testclass="com.blazemeter.jmeter.threads.concurrency.ConcurrencyThreadGroup" testname="some_scenario" enabled="true"><elementProp name="ThreadGroup.main_controller" elementType="com.blazemeter.jmeter.control.VirtualUserController"/><stringProp name="ThreadGroup.on_sample_error">continue</stringProp><stringProp name="TargetLevel">1</stringProp><stringProp name="RampUp">0</stringProp><stringProp name="Steps">0</stringProp><stringProp name="Hold">60</stringProp><stringProp name="LogFilename"></stringProp><stringProp name="Iterations"></stringProp><stringProp name="Unit">S</stringProp></com.blazemeter.jmeter.threads.concurrency.ConcurrencyThreadGroup><hashTree type="tg">
        <CacheManager guiclass="CacheManagerGui" testclass="CacheManager" testname="Cache">
          <boolProp name="clearEachIteration">true</boolProp>
          <boolProp name="useExpires">true</boolProp>
        </CacheManager>
        <hashTree/>
        <CookieManager guiclass="CookiePanel" testclass="CookieManager" testname="Cookies">
          <boolProp name="CookieManager.clearEachIteration">false</boolProp>
          <stringProp name="CookieManager.implementation">org.apache.jmeter.protocol.http.control.HC4CookieHandler</stringProp>
        </CookieManager>
        <hashTree/>
        <DNSCacheManager guiclass="DNSCachePanel" testclass="DNSCacheManager" testname="DNS Cache Manager">
          <collectionProp name="DNSCacheManager.servers"/>
          <boolProp name="DNSCacheManager.clearEachIteration">false</boolProp>
          <boolProp name="DNSCacheManager.isCustomResolver">false</boolProp>
        </DNSCacheManager>
        <hashTree/>
        <ConfigTestElement guiclass="HttpDefaultsGui" testclass="ConfigTestElement" testname="Defaults">
          <boolProp name="HTTPSampler.image_parser">true</boolProp>
          <boolProp name="HTTPSampler.concurrentDwn">true</boolProp>
          <stringProp name="HTTPSampler.concurrentPool">4</stringProp>
          <elementProp name="HTTPsampler.Arguments" elementType="Arguments" guiclass="HTTPArgumentsPanel" testclass="Arguments" testname="user_defined"/>
          <stringProp name="HTTPSampler.connect_timeout">30000</stringProp>
          <stringProp name="HTTPSampler.response_timeout">30000</stringProp>
        </ConfigTestElement>
        <hashTree/>
        <HTTPSamplerProxy guiclass="HttpTestSampleGui" testclass="HTTPSamplerProxy" testname="https://google.com">
          <stringProp name="HTTPSampler.protocol">https</stringProp>
          <stringProp name="HTTPSampler.domain">google.com</stringProp>
          <stringProp name="HTTPSampler.port"/>
          <stringProp name="HTTPSampler.path"/>
          <stringProp name="HTTPSampler.method">GET</stringProp>
          <boolProp name="HTTPSampler.use_keepalive">true</boolProp>
          <boolProp name="HTTPSampler.follow_redirects">true</boolProp>
          <boolProp name="HTTPSampler.auto_redirects">false</boolProp>
        </HTTPSamplerProxy>
        <hashTree/>
      </hashTree>
      <ResultCollector testname="View Results Tree" testclass="ResultCollector" guiclass="ViewResultsFullVisualizer" enabled="false"/>
      <hashTree/>
    <ResultCollector testname="KPI Writer" testclass="ResultCollector" guiclass="SimpleDataWriter"><stringProp name="filename">/var/taurus/logs/kpi.jtl</stringProp><objProp><name>saveConfig</name><value class="SampleSaveConfiguration"><xml>false</xml><fieldNames>true</fieldNames><time>true</time><timestamp>true</timestamp><latency>true</latency><connectTime>true</connectTime><success>true</success><label>true</label><code>true</code><message>true</message><threadName>true</threadName><dataType>false</dataType><encoding>false</encoding><assertions>false</assertions><subresults>false</subresults><responseData>false</responseData><samplerData>false</samplerData><responseHeaders>false</responseHeaders><requestHeaders>false</requestHeaders><responseDataOnError>false</responseDataOnError><saveAssertionResultsFailureMessage>false</saveAssertionResultsFailureMessage><bytes>true</bytes><hostname>true</hostname><threadCounts>true</threadCounts><url>false</url></value></objProp></ResultCollector><hashTree/><ResultCollector testname="Errors Writer" testclass="ResultCollector" guiclass="SimpleDataWriter"><stringProp name="filename">/var/taurus/logs/error.jtl</stringProp><objProp><name>saveConfig</name><value class="SampleSaveConfiguration"><xml>true</xml><fieldNames>true</fieldNames><time>true</time><timestamp>true</timestamp><latency>true</latency><success>true</success><label>true</label><code>true</code><message>true</message><threadName>true</threadName><dataType>true</dataType><encoding>true</encoding><assertions>true</assertions><subresults>true</subresults><responseData>false</responseData><samplerData>false</samplerData><responseHeaders>true</responseHeaders><requestHeaders>true</requestHeaders><responseDataOnError>true</responseDataOnError><saveAssertionResultsFailureMessage>true</saveAssertionResultsFailureMessage><bytes>true</bytes><threadCounts>true</threadCounts><url>true</url></value></objProp><boolProp name="ResultCollector.error_logging">true</boolProp></ResultCollector><hashTree/></hashTree>
  </hashTree>
</jmeterTestPlan>
```