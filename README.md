# attend_inven_helper
<div align=left> 
  <img src="https://img.shields.io/badge/python-43B02A?style=flat-square&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/selenium-3776AB?style=flat-square&logo=selenium&logoColor=white">
  <img src="https://img.shields.io/badge/RHEL-EE0000?style=flat-square&logo=red hat&logoColor=white">
  <br>
  <br>
</div>
This script automatically proceeds with login, check attendance, voting, dice, advertisement clicks, and brand partner clicks, helping you accumulate points.<br>

* * *

### Configuration

Edit \Script Directory\ .env

```env
WEBDRIVER_URL=http://***********:4444/wd/hub
INVEN_USERNAME=n*******
INVEN_PASSWORD=S***************************************************************
```

* * *

### How to use

Below is an example running using docker. Run it once a day using a scheduler such as crontab.

`/root/sh/attend_inven_helper.sh example`
```sh
#!/bin/bash
log_file=/tmp/attend_inven_helper.log
{
  echo "$0"
  docker run -i --rm --name=python-selenium-inven --user=0:0 --network g******* --env-file /data/python-selenium/.env \
  -v /data/python-selenium/data:/data:rw \
  python-selenium:latest \
  python /data/attend_inven_helper.py
} > $log_file
log=$(< $log_file tail -c 4096)
if [ -z "$log" ]; then
  exit 1
fi
/usr/bin/curl --data-urlencode text="$log" https://api.telegram.org/bot**********************************************/sendMessage?chat_id=**********
```

* * *

### Contact and license

<a href="mailto:xqbty8po-dntco43u@yahoo.com" target="_blank"><img src="https://img.shields.io/badge/yahoo!-6001D2?style=flat-square&logo=yahoo!&logoColor=white"/></a>
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
