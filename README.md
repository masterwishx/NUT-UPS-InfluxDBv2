## NUT in Grafana Dashboard

####  Description:

A comprehensive dashboard for visualizing data exported from Network UPS Tools (NUT) for UNRAID plugin or any other Linux system with NUT using InfluxDBv2 through Telegraf or similar tools. This dashboard leverages the NUT driver in Telegraf to collect UPS metrics and stores them in InfluxDB, which can then be visualized in Grafana.

- NUT -> Telegraf -> InfluxDBv2 -> Grafana

#### Key Features:

* Real-time Monitoring: Display real-time data from your UPS.
* Historical Data: Visualize historical UPS data over time.
* Customizable Dashboard: Tailor the dashboard to include specific metrics like voltage, current, load, and temperature.
* Integrations: Easily integrate with UNRAID or any Linux system running NUT.

### Grafana Dashboard ID: **[20846](https://grafana.com/grafana/dashboards/20846-nut-ups-telegraf/)**

<img width="2523" height="972" alt="Screenshot 2025-08-31 223538" src="https://github.com/user-attachments/assets/375366cb-0bf0-4a47-a4b3-a6273783678b" />
<img width="2522" height="1145" alt="Screenshot 2025-08-31 222731" src="https://github.com/user-attachments/assets/b52291f3-d0b1-4202-a126-758b28a85738" />
<img width="2530" height="904" alt="Screenshot 2025-08-31 223156" src="https://github.com/user-attachments/assets/9571e225-a49f-409f-b63b-71969f2078ac" />
<img width="2535" height="858" alt="Screenshot 2025-08-31 223204" src="https://github.com/user-attachments/assets/1e3de1db-77eb-4212-971a-44ad6e43015e" />

### Updates
- **31.8.25** - ``` Added more variables for Advanced UPS Info, Input/Output gauges now have symmetric thresholds with descriptions. Added Input/Output Voltage and Frequency Time Series panels with thresholds. Updated mapping values to use regex and more several fixes. ```<br>
- **17.3.25** - ``` Optimized static stat panels to show only the last values + some Fixes. ```<br>
- **27.9.24** - ``` Added Power Consumption - Costs UPS info panels. ```<br>
- **14.8.24** - ``` Added Some more Info + some Fixes. ```<br>
- **28.5.24** - ``` Added Multi bucket support. ```<br>

### Steps

 You can change bucket name and add multiple buckets by : 

 - <b>Go to Dashboard Setting - Variables - Click on bucket - Custom options:</b>

 ![image](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/a64a24e6-1be5-46d4-b0c1-7ea6b2da0716)

- add next to telegraf config: 

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

### Links

- [Network UPS Tools (NUT) for UNRAID by Rysz](https://forums.unraid.net/topic/60217-plugin-nut-v2-network-ups-tools/) <br>
- [Telegraf](https://github.com/influxdata/telegraf) <br>
- [Influxdb2](https://github.com/influxdata/influxdb) <br>
- [Grafana](https://github.com/grafana/grafana) <br>


### NUT-UPS-InfluxDBv2 (Old one)
A dashboard to display data exported from Network UPS Tools (NUT) for UNRAID
to InfluxDBv2 by nut-influxdbv2. Avalible Now at Grafana Dashboard 20077

![Screenshot 2023-12-03 212110](https://github.com/masterwishx/NUT-UPS-InfluxDBv2/assets/28630321/2732331e-59a0-437d-ad27-87a241d63de7)

### Links

- Network UPS Tools (NUT) for UNRAID by Rysz - https://forums.unraid.net/topic/60217-plugin-nut-v2-network-ups-tools/ <br>
- nut-influxdbv2 - https://hub.docker.com/r/jwillmer/nut-influxdbv2



