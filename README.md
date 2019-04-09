# wms-performance-testing

```
exo config
```
```
exo vm template list
```

```
exo firewall create demo-securitygroup
exo firewall add demo-securitygroup ssh 
exo firewall add demo-securitygroup http

exo vm create qgis-micro -f user-data.txt -d 50 -o micro -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup
exo vm create qgis-micro -d 50 -o micro -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup
```

```
exo ssh qgis-micro
```

