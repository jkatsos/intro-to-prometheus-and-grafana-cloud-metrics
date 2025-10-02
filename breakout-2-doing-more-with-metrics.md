# Breakout 2 - Doing more with Metrics in Grafana Cloud

Navigate to the Grafana AI & Machine learning page

![Node exporter metrics](images/image27.png)

From here you can see all the AI & ML capabilities that Grafana Cloud offers across the platform.

Spend some time here exploring some of the capabilities on offer.

For this excercise we will use the Load Balanace Average latency query we created earlier to predict unexpected increases in latency

1. Click + New Forecast.
2. In the Query builder, choose the promethues datasource that we created earlier.
3. Run the following query:

```bash
sum(rate(tns_request_duration_seconds_sum{job="tns-loadgen"}[1m])) * 1e3 / sum(rate(tns_request_duration_seconds_count{job="tns-loadgen"}[1m]))
```

4. Click Next: Preview and tune.
5. Preview the forecast. Your series appears in green while the forecast is blue.
6. Drag the Uncertainty interval width slider to 0.8 and see how the bands in the preview get narrower.
7. Click the Advanced Model Options section header and observe the tuneable knobs.
8. Click Next: Set name and description.
9. Name your forecast Grafana Cloud Active Series and click Next: Review.
10. Review your forecast. Once you’re satisfied, click Create forecast.
11. On the Forecasts page, your forecast is ready to generate predictions when the Pending tag turns into a green Ready tag.

# View your forecast
Click View on the Grafana Cloud Active Series forecast you created in the previous section.
Change the view to an interesting time frame for your forecast. By default the view is for the current week.
Explore how the forecast matches your actual result, and be sure to include some days in the future to see how the model thinks your active series will evolve.

At the top of the screen, the UI displays your original query, as well as how you can query the forecast (grafanacloud_active_series:predicted) or actual(grafanacloud_active_series:actual) data. You can use these series to create panels or alerts.

It should look something like this:
![Node exporter metrics](images/image28.png)

# Use the forecast in a panel
From the view page:

1. Click the Copy as panel button in the upper right.
2. Open an existing dashboard or create a new dashboard.
3. At the top of the dashboard, click Add and select Paste panel from the dropdown.
4. Edit the new panel and view the generated queries.

# [Advanced to do later] Use the forecast in an alert
[Grafana Alerting](https://grafana.com/docs/grafana/latest/alerting/#overview-of-grafana-alerting)

1. Click the Create Alert button from either the view page or the list page.
2. In the Alert evaluation behavior section, choose a folder in which to save the alert.
3. Tune the alert conditions and labels, if desired.
4. Click Save or Save and exit to create the alert and navigate back to the previous page.


## Pop Quiz
What query would you use to find the Prometheus build info?

How many time series does this Prometheus server have?

## End of second breakout. Stop here!

---
```























```
## Answer to the Pop Quiz
```
prometheus_build_info
```

`prometheus_tsdb_head_series` to find `3100`
