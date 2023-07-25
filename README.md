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
![Captura de tela de 2021-12-17 07-52-37](https://user-images.githubusercontent.com/87427032/146535570-e6e25c72-cd0d-4a8d-bea4-469745521e77.png)
- Iniciando em modo demond (2º plano).
```
#docker-compose up -d   
```
![Captura de tela de 2021-12-17 07-53-05](https://user-images.githubusercontent.com/87427032/146535579-0caf4ddb-956c-4140-8746-2b72fcb40319.png)
### Verificando os containers
- Listand os containers em execução.
```
#docker container ls                       
```
![Captura de tela de 2021-12-17 07-53-22](https://user-images.githubusercontent.com/87427032/146535637-d6025194-3015-440d-8b71-b440e1eac43b.png)
- Visualizando os logs do serviço em execução.
```
#docker container logs -f ID_Container     #Opção -f retorna o que é acrescentado de novo ao arquivo de log da aplicação.
```
![Captura de tela de 2021-12-17 07-56-08](https://user-images.githubusercontent.com/87427032/146535723-58e1694f-81e2-4530-9440-87a9ff4530b7.png)
- Trazendo detalhamento do container.
```
#docker container inspect ID_Container
```
![Captura de tela de 2021-12-17 07-58-05](https://user-images.githubusercontent.com/87427032/146535780-08dea5a3-db15-4f80-bbd3-898e893272bc.png)
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
