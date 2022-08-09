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

## Usage from "beerpiss/autotss-cli"

<details>
  <summary>On *nix systems (cron)</summary>

- Install cron on your system
- Add `*/10 * * * * /bin/bash -c "cd AUTOTSS_DIR && python3 autotss.py"` to your crontab
  - Replace `AUTOTSS_DIR` with the full path to your AutoTSS-CLI folder
  - This runs every 10 minutes, but the frequency can be altered by changing the `10` in `*/10` to a different number of minutes.
</details>

<details>
  <summary>On systemd-based systems</summary>

- Create a new service file (e.g. `/etc/systemd/system/autotss.service`):  
Replace `<AUTOTSS_DIR>` with the full path to your AutoTSS-CLI folder, and `<username>` and `<group>` with your own information (usually you can use your username for both).  
It runs every 10 minutes (600 seconds), but you can edit `RestartSec=` to a different number of seconds.
```ini
[Unit]
Description=autotss
After=multi-user.target
After=network-online.target
Wants=network-online.target

[Service]
WorkingDirectory=<AUTOTSS_DIR>
ExecStart=/usr/bin/python3 autotss.py
User=<username>
Group=<group>
Type=simple
Restart=always
RestartSec=600
TimeoutStopSec=10

[Install]
WantedBy=multi-user.target
```
- Reload all service files: `sudo systemctl daemon-reload`
- Enable and start the service: `sudo systemctl enable --now autotss`
</details>

<details>
  <summary>On Windows systems</summary>

- Open Task Scheduler (taskschd.msc)
- Create a task:
   - Trigger:
       - Begin the task: At task creation/modification
       - Repeat task every: 10 minutes
       - For a duration of: Indefinitely
   - Actions:
       - Action: Start a program
       - Program/script: <path to your python.exe>
       - Add arguments: autotss.py
       - Start in: <path to your AutoTSS-CLI folder>
</details>

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

## Requirements from "beerpiss/autotss-cli"
* python 3
* cron (optional, but recommended for full automation)
* [libimobiledevice](https://github.com/libimobiledevice/libimobiledevice/)  
If you're on Windows:  
```
scoop bucket add beerpiss https://github.com/beerpiss/scoop-bucket
scoop install beerpiss/libimobiledevice
```
* [tsschecker](https://github.com/1Conan/tsschecker/) (1Conan's updated fork, as tihmstar's is outdated)
