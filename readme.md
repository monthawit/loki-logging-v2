Openshift send log to external log 

https://www.redhat.com/en/blog/openshift-logging-forwarding-logs-to-external-loki

config Promtail 

https://github.com/grafana/loki/issues/1165#issuecomment-700129425 

=========================================

helm repo add grafana https://grafana.github.io/helm-charts


helm repo update

helm search repo grafana/loki --versions

helm install --values loki-values.yaml loki grafana/loki -n loki 

 *** specific version *** 

helm search repo grafana/loki --versions

helm install --values loki-values.yaml loki grafana/loki -n loki --version CHART-VERSION-number

=======================================

Install Promtail On VM     

https://levelup.gitconnected.com/how-to-setup-grafana-loki-for-free-log-management-ceb60558503c 

$ sudo cat <<EOF >/etc/systemd/system/promtail.service
[Unit] 
Description=Promtail service 
After=network.target 
 
[Service] 
Type=simple 
#User=promtail 
ExecStart=/opt/loki/promtail-linux-amd64 -config.file /opt/loki/promtail-local-config.yaml 
Restart=always 
 
[Install] 
WantedBy=multi-user.target
EOF
$ sudo systemctl start promtail.service
$ sudo systemctl enable promtail.service



==================  limit ======

https://community.grafana.com/t/discarding-promtail-log-entries-en-masse/41128/3 


============ Promtail Grafana Dashboard ID ==============

16966 

https://grafana.com/grafana/dashboards/16966-container-log-dashboard/ 

==================== Connection ====================

=== Send To log server ====

https://loki-gateway.observe.olsdemo.com/loki/api/v1/push

=== Connect By Grafana ===

http://loki-gateway.loki.svc.cluster.local
