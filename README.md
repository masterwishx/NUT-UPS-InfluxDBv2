## NUT-UPS-Telegraf-InfluxDBv2
A dashboard to display data exported from Network UPS Tools (NUT) for UNRAID
to InfluxDBv2 by upsd in Telegraf Avalible Now at Grafana Dashboard 20846

![Screenshot 2024-09-27 210635-2](https://github.com/user-attachments/assets/e7c55917-1e56-4024-85bc-dd79294c0968)
![Screenshot 2024-09-27 211641](https://github.com/user-attachments/assets/2b088b64-fd0d-42ad-9443-2496f1c1daa9)
![Screenshot 2024-09-27 211653](https://github.com/user-attachments/assets/c9f9da93-95ce-44a9-97f7-0da92f178b29)

## Updates
``` 27.9.24 - Added Power Consumption - Costs UPS info panels. ```<br>
``` 14.8.24 - Added Some more Info + some Fixes. ```<br>
``` 28.5.24 - Added Multi bucket support. ```<br>

## Steps

 You can change bucket name and add multiple buckets by : 

 <b>Go to Dashboard Setting - Variables - Click on bucket - Custom options:</b>

 ![image](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/a64a24e6-1be5-46d4-b0c1-7ea6b2da0716)

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
## NUT-UPS-InfluxDBv2
A dashboard to display data exported from Network UPS Tools (NUT) for UNRAID
to InfluxDBv2 by nut-influxdbv2. Avalible Now at Grafana Dashboard 20077

Network UPS Tools (NUT) for UNRAID by Rysz - https://forums.unraid.net/topic/60217-plugin-nut-v2-network-ups-tools/ <br>
nut-influxdbv2 - https://hub.docker.com/r/jwillmer/nut-influxdbv2


![Screenshot 2023-12-03 212110](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/2732331e-59a0-437d-ad27-87a241d63de7)




