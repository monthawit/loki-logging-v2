helm repo add grafana https://grafana.github.io/helm-charts


helm repo update


helm install --values loki-values.yaml loki grafana/loki -n loki



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
