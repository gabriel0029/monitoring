Projeto de monitoramento docker

docker compose pull
docker compose up -d

Acesso do grafana:
http://seu_ip:3000
admin
suporte


para coletar os logs dos container em execução acrescentel os lables

logging: "promtail"
logging_jobname: "containerlogs"