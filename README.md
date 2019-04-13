# wms-performance-testing

```
exo config
```
```
exo vm template list
exo vm serviceoffering
```

```
exo firewall create demo-securitygroup
exo firewall add demo-securitygroup ssh 
exo firewall add demo-securitygroup http

exo vm create qgis-micro -f user-data.yml -d 50 -o micro -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup
exo vm create qgis-micro -d 50 -o micro -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup


exo vm create jmeter-large -f /vagrant/user-data/jmeter/user-data.yml -d 50 -o large -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup

exo vm create qgis-medium -f /vagrant/user-data/qgis-server/user-data.yml -d 100 -o medium -t "Linux Ubuntu 18.04 LTS 64-bit" --security-group demo-securitygroup



```

```
exo ssh qgis-micro
```


## QGIS server

Manuelle Schritte auf Server:
```
cd /data
wget https://sos-ch-dk-2.exo.io/ch.so.agi.orthofoto-2015.rgb/ch.so.agi.orthofoto_2015.rgb.gpkg
wget https://sos-ch-dk-2.exo.io/ch.so.agi.orthofoto-2016.rgb/ch.so.agi.orthofoto_2016.rgb.gpkg
wget https://sos-ch-dk-2.exo.io/ch.so.agi.orthofoto-2017.rgb/ch.so.agi.orthofoto_2017.rgb.gpkg
wget https://sos-ch-dk-2.exo.io/ch.so.agi.wms-performance-test/orthofoto_gpkg.qgs 
wget https://sos-ch-dk-2.exo.io/ch.so.agi.wms-performance-test/orthofoto_geotiff_34.qgs 
wget https://sos-ch-dk-2.exo.io/ch.so.agi.wms-performance-test/orthofoto_geotiff_218.qgs 
cd ..
chmod -R 777 data/
cd
docker run -p 80:80 -v /data:/data -e QGIS_FCGI_MIN_PROCESSES=2 -e QGIS_FCGI_MAX_PROCESSES=2 sogis/qgis-server-base:3.4
```


194.182.165.160


## jmeter machine

Ssh key aus der lokalen Vagrant-Maschine auf lokalen Rechner kopieren, damit x2goclient Zugriff hat. Instance-Id (und IP) ändert sich natürlich.
```
cp /home/vagrant/.config/exoscale/instances/f686dc99-f7f2-448f-af22-46c164679de2/id_rsa /vagrant/
```

Manuelle Schritte auf Server:
```
git clone https://github.com/edigonzales/wms-performance-testing.git
```




jmeter -g <log file> -o <Path to output folder>

docker run -p 80:80 -v /data:/data -e QGIS_FCGI_MIN_PROCESSES=2 -e QGIS_FCGI_MAX_PROCESSES=2 sogis/qgis-server-base:3.4
docker run -p 80:80 -v /data:/data -e QGIS_FCGI_MIN_PROCESSES=2 -e QGIS_FCGI_MAX_PROCESSES=2 sogis/qgis-server-base:2.18

ssh -i "/home/vagrant/.config/exoscale/instances/c4fe99b1-1dc9-414f-954e-c7830ba81195/id_rsa" ubuntu@194.182.165.135
ssh -i "/home/vagrant/.config/exoscale/instances/82c506b2-1700-4d87-a53a-630d4099ec1d/id_rsa" ubuntu@194.182.165.160