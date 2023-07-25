# Projeto de monitoramento docker

# Preparação do ambiente

### Instalação Docker
```
curl -fsSL https://get.docker.com/ | sh
```
Obs: Instalará a versão mais recente.


## Docker Compose
### instalação 
```
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

## Docker-compose
Caso use o docker compose faça o download dos arquivos, eles se encontram logo acima. aṕos isso entre no diretório para que possamos executar os containers. 

### Execudando o container
- Fazer o download das imagens dos containers.
```
#docker-compose pull 
```
- Iniciando em modo demond (2º plano).
```
#docker-compose up -d   
```
### Verificando os containers
- Listand os containers em execução.
```
#docker container ls                       
```
- Visualizando os logs do serviço em execução.
```
#docker container logs -f ID_Container ou nome_container 
```
A opção -f retorna o que é acrescentado de novo ao arquivo de log da aplicação.

- Trazendo detalhamento do container.
```
#docker container inspect ID_Container
```
- Status dos containers.
```
#docker container stats                    
```

### finalizando container
- Finalizando (desligando), os containers.
```
#docker-compose stop     
```
- Finalizando e apagando tudo relacionado aos containers.
```
#docker-compose down     
``` 

### Primeiro acesso

- Acesso do grafana:
```
http://seu_ip:3000
```
admin  
suporte

- Obs. Para coletar os logs dos containers em execução acrescente os lables a seus containers

```
logging: "promtail" e 
logging_jobname: "containerlogs"
```
