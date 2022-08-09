# Cron

## Content

files :
```
/srv/autotss/devices.json
/srv/autotss/autotss.py
```

`crontab -l` :
```
# m h  dom mon dow   command
*/10 * * * *	/bin/bash -c "cd /srv/autotss && /usr/bin/python3 autotss.py > run.log" >/srv/autotss/cron.log 2>&1
```

## Ubuntu

cron.service

## Fedora Silverblue

crond.service

`sudo rpm-ostree install -A cronie-anacron cronie`.

