# date

update date on server at the time of restart:
```bash
cat << EOF > /etc/init.d/update-date
date --set="\$(curl -I 'https://google.com/' 2>/dev/null | grep -i '^date:' | sed 's/^[Dd]ate: //g')"
EOF
sudo chmod +x /etc/init.d/update-date
```

update time from server:
```bash
date --set="$(curl -I 'https://google.com/' 2>/dev/null | grep -i '^date:' | sed 's/^[Dd]ate: //g')"
```

Display date and time:
```bash
date

# Coordinated Universal Time
# GMT == UTC
# UTC time. This is used mostly on servers.
date -u

# Indian Standard Time
TZ=Asia/Kolkata date

# Japan Standard Time
TZ=Asia/Tokyo date
```

generate random pasword:
```bash
date +%s%N | md5sum | awk '{print $1}'
date +%s%N | sha256sum | awk '{print $1}'

while true; do date +%s%N | md5sum | awk '{print $1}'; done
while true; do date +%s%N | sha256sum | awk '{print $1}'; done
```

https://en.wikipedia.org/wiki/List_of_tz_database_time_zones

