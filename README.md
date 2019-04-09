# wms-performance-testing

```
exo config
```
```
exo vm template list
```

```
exo firewall create demo-securitygroup
exo firewall add demo-securitygroup ssh --my-ip
exo firewall add demo-securitygroup http

exo vm create qgis-micro -f user-data.txt -d 50 -o micro -t "Linux Ubuntu 18.04 LTS 64-bit"
```

```
exo ssh qgis-micro
```
