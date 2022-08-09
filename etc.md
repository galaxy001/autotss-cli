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


# Build

## Fedora Silverblue

```sh
sudo rpm-ostree install make automake gcc gcc-c++ autoconf libtool
sudo rpm-ostree install python3-devel libcurl-devel libzip-devel zlib-devel openssl-devel
sudo rpm-ostree install libplist-devel libirecovery-devel

git clone https://github.com/tihmstar/tsschecker.git
git clone https://github.com/tihmstar/libfragmentzip.git
git clone https://github.com/tihmstar/libgeneral.git
git clone https://github.com/galaxy001/autotss-cli.git
```

## Ubuntu

```sh
sudo apt install build-essential checkinstall git autoconf automake libtool-bin
sudo apt install python3-dev libcurl4-openssl-dev libzip-dev libssl-dev libreadline-dev libusb-1.0-0-dev

git clone https://github.com/tihmstar/tsschecker.git
git clone https://github.com/tihmstar/libfragmentzip.git
git clone https://github.com/tihmstar/libgeneral.git
git clone https://github.com/galaxy001/autotss-cli.git

git clone https://github.com/libimobiledevice/libplist.git
git clone https://github.com/libimobiledevice/libimobiledevice-glue.git
git clone https://github.com/libimobiledevice/libirecovery.git
```

## Forks

###  tihmstar / tsschecker

* <https://github.com/DanTheMann15/tsschecker/tree/development>
* <https://github.com/1Conan/tsschecker>

## m1stadev / autotss-cli

* <https://github.com/beerpiss/autotss-cli>
* <https://github.com/galaxy001/autotss-cli>

See also <https://github.com/airsquared/blobsaver> and <https://github.com/m1stadev/AutoTSS>.
