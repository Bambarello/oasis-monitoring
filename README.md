# Oasis-monitoring

1) using standard prometheus collector and grafana
2) install node_exporter to the oasis node
3) expose metrics from oasis-node

 Example of oasis-node parameter to expose the metrics
 
 ```
 ExecStart=/home/oasis/oasis-node \
        --config /home/oasis/serverdir/etc/config.yml \
        --metrics.mode pull \ 
        --metrics.address 0.0.0.0:9101 
```
