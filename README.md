# Projeto de monitoramento usando docker

## Preparação do ambiente

### Instalação Docker
```
curl -fsSL https://get.docker.com/ | sh
```
Obs: Instalará a versão mais recente.


#### Dica importante
Por padrão, o daemon do Docker faz bind em um socket Unix, e não em uma porta TCP. Sockets Unix, por sua vez, são de propriedade e de uso exclusivo do usuário root (por isso o Docker sempre é iniciado como root), mas também podem ser acessados através do sudo por outros usuários.

Para evitar que você tenha que ficar usando sudo ao rodar comandos do Docker, crie um grupo chamado docker e adicione o seu usuário a ele. Pare o serviço e inicie-o novamente.

Esse procedimento faz com que o usuário tenha os mesmos privilégios do usuário root em operações relacionadas ao Docker. Mais informações no link: https://docs.docker.com/engine/security/.

Para criar um grupo no Linux e adicionar um usuário:
```
$ sudo usermod -aG docker user
```
Dica de para passar de ano: **user** = seu usuário.


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
### Verificando os containers em execução
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

Obs. Para coletar os logs dos containers em execução acrescente os lables.

```
logging: "promtail" e
logging_jobname: "containerlogs"
```
### Exemplo

Docker run

```
docker run -d -p80:80 --name nginx --label logging=promtail --label logging_jobname=containerlogs nginx
```
Dentro .ymal na seção do container

```
labels:
  logging: "promtail"
  logging_jobname: "containerlogs"
```
