# NUT-UPS-InfluxDBv2
A dashboard to display data exported from Network UPS Tools (NUT) for UNRAID
to InfluxDBv2 by nut-influxdbv2. Avalible Now at Grafana Dashboard 17808

Network UPS Tools (NUT) for UNRAID by Rysz - https://forums.unraid.net/topic/60217-plugin-nut-v2-network-ups-tools/ <br>
nut-influxdbv2 - https://hub.docker.com/r/jwillmer/nut-influxdbv2


![Screenshot 2023-12-03 212110](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/2732331e-59a0-437d-ad27-87a241d63de7)

# NUT-UPS-Telegraf-InfluxDBv2
A dashboard to display data exported from Network UPS Tools (NUT) for UNRAID
to InfluxDBv2 by upsd in Telegraf Avalible Now at Grafana Dashboard 20846

![Screenshot 2024-04-06 113839](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/4f36302f-c8d1-48b4-8deb-8ca3ce452811)


addd next to telegraf config: 

```
# Monitor UPSes connected via Network UPS Tools
[[inputs.upsd]]
  ## A running NUT server to connect to.
  ## IPv6 addresses must be enclosed in brackets (e.g. "[::1]")
   server = "your IP"
   port = 3493
  # username = "user"
  # password = "password"

   additional_fields = ["*"]

# Map enum values according to given table.
  ## ## UPS beeper status (enabled, disabled or muted)
  ## Convert 'enabled' and 'disabled' values back to string from boolean
[[processors.enum]]
  [[processors.enum.mapping]]
    field = "ups_beeper_status"
    [processors.enum.mapping.value_mappings]
      true = "enabled"
      false = "disabled"

[[outputs.influxdb_v2]]
  ## The URLs of the InfluxDB cluster nodes.
  ## Add all your info for influxDbv2
```




