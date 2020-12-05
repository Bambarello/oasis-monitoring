# Oasis-monitoring

1) Use standard Grometheus mettics collector and Grafana.
2) Install *node_exporter* to the oasis node. Default port for metrics is 9100.
3) Expose metrics from oasis-node.

 Example of oasis-node parameter to expose the metrics. You may change the port to any.
 
 ```
 ExecStart=/home/oasis/oasis-node \
        --config /home/oasis/serverdir/etc/config.yml \
        --metrics.mode pull \ 
        --metrics.address 0.0.0.0:9101 
```
 
4) Update the prometheus.yml to grab node_exporter and oasis_node metrics. 
**Important**: ensure you clearly indicate "Job" as "oasis" for proper grafana dashboard functionality.

```
      - targets: ['[NODE IP]:9100']
        labels:
          host: "Oasis System"
          job: "oasis"
      - targets: ['[NODE IP]:9101']
        labels:
          host: "Oasis Node"
          job: "oasis"
```
