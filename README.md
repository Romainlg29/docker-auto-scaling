
# Docker auto scaling

#### An automatic python script that scales up or down services based on CPU usage.

Thresholds: < 30% on average service will scale down and 70% > will scale up




## Installation

To run this script, you must install the following packages.

```bash
  apt install python3
  pip install docker
```
    
## Usage/Examples

```bash
# Using once

python3 auto-scaling.py
```

```bash
# Using every X seconds

python3 auto-scaling.py -t 30
```

```bash
# Using CRON
# It'll run every minutes

*     *     *     *     *         python3 auto-scaling.py
```

```bash
# Using TIMER
# It'll run every minutes

#scaling.service
[Unit]
Description=Docker scaling script

[Service]
Type=oneshot
ExecStart=/usr/bin/python3 /.../auto-scaling.py

#scaling.timer
[Unit]
Description=Docker scaling script

[Timer]
OnCalendar=*-*-* *:*:00

[Install]
WantedBy=timers.target

# CLI
systemctl enable /.../scaling.timer

```

