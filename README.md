# nuage-prom-collector

Prometheus Node Exporter collector for the metrics from Nuage Networks
Virtualized Services Platform (VSP).

## Getting Started

First, install Nuage Python SDK, i.e. `vspk`:

```
pip install vspk ipaddress
```

Next, configure credentials:

```
cat << EOF > ~/.nuage_api.cfg
[default]
password = "My@Secret"
EOF
chmod 600 ~/.nuage_api.cfg
```

Then, clone this project:

```
cd /opt && git clone git@github.com:greenpau/nuage-prom-collector.git
```

Finally, run the collection:

```
/opt/nuage-prom-collector/nuage-prom-collector --output /var/lib/prometheus --file localhost
```

Alternatively, schedule data collection every 5 minutes with `cron`:

```
*/5 * * * * /opt/nuage-prom-collector/nuage-prom-collector --output /var/lib/prometheus --file localhost
```

The below are usage instructions:

```
usage: nuage-prom-collector [-h] [--host IP_OR_NAME] [--port NUMBER]
                            [--enterprise NAME] [--user NAME] [--file NAME]
                            [--output PATH] [-l LEVEL] [--sanity-check]

nuage-prom-collector - Prometheus Exporter for Nuage VSP

optional arguments:
  -h, --help            show this help message and exit

Prometheus Exporter for Nuage VSP arguments:
  --host IP_OR_NAME     Nuage VSD API Host
  --port NUMBER         Nuage VSD API Port
  --enterprise NAME     Nuage VSD Enterprise
  --user NAME           Nuage VSD API User

Output:
  --file NAME           file name, suffix .prom is added automatically
  --output PATH         output directory

Logging and Debugging:
  -l LEVEL, --log-level LEVEL
                        Log level (default: 0, max: 2)
  --sanity-check        check field types against received values

contacts: Paul Greenberg (@greenpau)

examples:

    $ nuage-prom-collector --output /var/lib/prometheus
    $ nuage-prom-collector --output /var/lib/prometheus --file localhost
```
