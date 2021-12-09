Docker set up for home lab monitoring

Stack:
    Prometheus: Metrics
    Loki: Logs
    promtail: More log scraping
    Grafana: Dashboards / analysis
    OpenTelemetry: metrics format conversion
    snmp-exporter: publish prometheus stats from snmp (router stats)
    pi-hole-exporter: dashboarding for pi-hole based dashboarding

Enviroment variables
This file is intentionally NOT stored in the repository to prevent passwords and other senstive information from being imported into this repository. Username and password must be configured for the pi-hole scraper. Storage can be set to what ever location is desired

.env is as follows:
```
PI_HOLE_USERNAME=username 
PI_HOLE_PASSWORD=password

LOKI_STORAGE=~/homelab-monitoring/loki/
PROMTAIL_STORAGE=~/homelab-monitoring/promtail/
GRAFANA_STORAGE=~/homelab-monitoring/grafana/
PROMETHEUS_STORAGE=~/homelab-monitoring/prometheus/


```


Setup outside repository
    SNMP has to be enabled on router to get any data
    Proxmox external metrics must be set up for the influxdb import 
        use HTTP import
    promtail is configured to scrape docker logs from the host machine.
        Configuration instructions are available here: https://techno-tim.github.io/posts/grafana-loki/
            See "Loki Docker Driver"

Storage:


Ports exposed on host machine.
    This is mostly to 
    3100 : Loki
    3000 : grafana 
    9090 : Prometheus
    9116 : snmp exporter
    9617 : pi-hole-exporter

    8086 : otel Influx reciever
    8888 : otel prometheus metrics
    9101 : prometheus metrics from influx metrics
    13133: otel healthcheck
    55679: otel zpages for trouble shooting

Internal network ports:
