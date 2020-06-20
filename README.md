# purge-openproject
Purge openproject from ubuntu 18.04

```
sudo su -

systemctl list-units --type service |grep -iH openproject

systemctl disable openproject-web-1.service
systemctl disable openproject-web.service
systemctl disable openproject-worker-1.service
systemctl disable openproject-worker.service
systemctl disable openproject.service

service openproject stop

rm -rf /opt/openproject

userdel openproject

rm -rf /home/openproject

rm -f /etc/cron.d/openproject-*

rm -f /etc/systemd/system/openproject*

rm -f /etc/apt/sources.list.d/openproject-ce.list

rm -rf /var/log/openproject
```

if using mysqk database:
```
mysql -u root
drop database openproject;
quit
```

if using postgresql database :
```
sudo su - postgres
psql
\l
drop databas openproject;
\q
exit
```

continue :
```
rm -rf /etc/openproject

rm -rf /var/db/openproject

dpkg --purge openproject

rm -f /var/lib/apt/lists/dl.packager.io_srv_deb_opf_openproject-*

rm -f /var/cache/apt/archives/openproject_*
```

Done.
