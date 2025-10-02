# Breakout 3 - The Grafana Assistant Challenge!

Navigate to the Grafana AI & Machine learning page

![Node exporter metrics](images/image27.png)

From here you can see all the **AI & ML capabilities that Grafana Cloud** offers across the platform.

Spend some time here exploring some of the capabilities on offer.

For this excercise we will use the Load Balanace Average latency query we created earlier to predict unexpected increases in latency

1. Click + New Forecast.
2. In the Query builder, choose the promethues datasource that we created earlier.
3. Run the following query:

```bash
sum(rate(tns_request_duration_seconds_sum{job="tns-loadgen"}[1m])) * 1e3 / sum(rate(tns_request_duration_seconds_count{job="tns-loadgen"}[1m]))
```
