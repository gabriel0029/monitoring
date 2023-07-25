Projeto de monitoramento docker

docker compose pull
docker compose up -d

Acesso do grafana:
http://seu_ip:3000
admin
suporte


para coletar os logs dos containers em execução acrescente os lables 

logging: "promtail" e 
logging_jobname: "containerlogs"