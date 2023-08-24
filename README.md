# Deimos

Deimos is a modified version of sidekick tailored to work seamlessly with KubeArmor. It acts as an intermediary to channel the alerts and logs from KubeArmor, facilitating broader integration and alerting capabilities.


## how to run DEIMOS(sidekick) (example used: SYSLOG)

### 1) install karmor 
```
karmor install 
```

### 2) run deimos 

#### 2.1) install deimos using Helm 

```
git clone https://github.com/Shreyas220/Deimos.git
```

```
git clone https://github.com/Shreyas220/Deimos.git
cd deimos
```

```
helm install deimos ./helm/deimos/ --set config.syslog.host=syslog-server-service.default.svc.cluster.local --set config.syslog.port=514 --set config.syslog.format=cef --set config.syslog.protocol=udp --set config.policyreport.enabled=true -n kube-system
```

To send alerts or log syslog you need these 4 parameters 
- host - ip address we are sending the events to. In k8s env the syslog server would have a service, you can provide the that here
- Port
- format: it supports 2 format 1)JSON 2)CEF. By default it is JSON please mention cef if you want to use it
- protocol: it supports 2 format 1)TCP 2)UDP 
