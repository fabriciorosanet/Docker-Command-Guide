# Docker-Command-Guide
Documento para consulta de comandos de forma mais ágil 
# Comandos `docker build`

| Comando                                                                                     | Explicação                                                                |
|---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| `docker build`                                                                              | Constrói uma imagem a partir de um Dockerfile (arquivo Docker) no diretório atual. |
| `docker build https://github.com/docker/rootfs.git#container:docker`                       | Constrói uma imagem a partir de um repositório Git remoto.                 |
| `docker build -t imagename/tag`                                                            | Constrói e identifica uma imagem, atribuindo uma tag para facilitar o monitoramento. |
| `docker build https://yourserver/file.tar.gz`                                              | Constrói uma imagem a partir de um arquivo tar remoto.                     |
| ```docker build -t image:1.0-<<EOF FROM busybox RUN echo "hello world" EOF```              | Constrói uma imagem a partir de um Dockerfile enviado via STDIN.           |

# Comandos de `Limpeza`

Limpar ou remover imagens, containers e volumes não utilizados é uma ótima maneira de economizar espaço em disco e manter seu sistema limpo e bem organizado. Confira abaixo alguns exemplos de comandos de natureza "clean up":

| Comando                                                              | Explicação                                                                                                           |
|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `docker image prune`                                                 | Remove uma imagem que não está sendo utilizada.                                                                     |
| `docker image prune -a`                                              | Remove todas as imagens que não estão sendo usadas por containers.                                                  |
| `docker system prune`                                                | Remove todos os containers pausados (stopped containers), todo o cache de construção (build cache), todas as redes não utilizadas por containers e todas as imagens sem tags (dangling images). |
| `docker image rm image`                                              | Remove uma imagem.                                                                                                  |
| `docker rm container`                                                | Remove um container que está rodando.                                                                               |
| `docker kill $(docker ps -q)`                                        | Pausa todos os containers que estão rodando.                                                                        |
| `docker swarm leave`                                                 | Sai do modo swarm.                                                                                                  |
| `docker stack rm stackname`                                          | Remove um swarm.                                                                                                    |
| `docker volume rm $(docker volume ls -f dangling=true -q)`           | Remove todos os volumes sem tags (dangling volumes).                                                                |
| `docker rm $(docker ps -a -q)`                                       | Remove todos os containers pausados.                                                                                |

Aqui está a tabela formatada em Markdown para o seu README no GitHub:


# Comandos de `Interação com Container`

Interaja com seu container Docker através dos comandos mais populares, como:

| Comando                                                                                               | Explicação                                                                                               |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `docker start container`                                                                             | Inicia um novo container.                                                                               |
| `docker stop container`                                                                              | Encerra (stop) um container.                                                                            |
| `docker pause container`                                                                             | Pausa um container.                                                                                     |
| `docker unpause container`                                                                           | Encerra a pausa de um container.                                                                        |
| `docker restart container`                                                                           | Reinicia um container.                                                                                  |
| `docker wait container`                                                                              | Bloqueia um container.                                                                                  |
| `docker export container`                                                                            | Exporta conteúdos de um container para um arquivo tar.                                                  |
| `docker attach container`                                                                            | Anexa conteúdo a um container que já está rodando (running container).                                  |
| `docker wait container`                                                                              | Coloca o processo em aguardo até que o container termine e exibe o exit code (código de saída).         |
| `docker commit -m "commit message" -a "author" container username/image_name:tag`                    | Salva um container que está rodando em formato de imagem.                                               |
| `docker logs -ft container`                                                                          | Acompanha logs de um container (registros).                                                             |
| `docker exec -ti container script.sh`                                                                | Roda um comando em um container.                                                                        |
| `docker commit container image`                                                                      | Cria uma nova imagem a partir de um container.                                                          |
| `docker create image`                                                                                | Cria um novo container a partir de uma imagem.                                                          |

# Comandos de Inspeção de Container

Às vezes, você pode precisar inspecionar seus containers para garantir a qualidade ou para resolver alguma falha. Os comandos abaixo te ajudam a entender melhor o que diferentes containers estão rodando:

| Comando                    | Explicação                                                                                   |
|----------------------------|-----------------------------------------------------------------------------------------------|
| `docker ps`                | Lista todos os containers que estão rodando (running containers).                            |
| `docker ps -a`             | Lista todos os containers.                                                                   |
| `docker diff container`    | Inspeciona alterações em diretórios e arquivos do sistema de arquivos do container.          |
| `docker top container`     | Exibe todos os processos que estão rodando em um container ativo.                            |
| `docker inspect container` | Exibe informações básicas (low-level information) sobre um container.                        |
| `docker logs container`    | Reúne os registros (logs) de um container.                                                   |
| `docker stats container`   | Exibe as estatísticas de consumo de recursos de um container.                                |

# Comandos de Gerenciamento de Imagens

Alguns dos comandos mais populares para administrar Docker images incluem:

| Comando                 | Explicação                                                             |
|-------------------------|-------------------------------------------------------------------------|
| `docker image ls`       | Lista imagens.                                                        |
| `docker image rm mysql` | Remove uma imagem.                                                    |
| `docker tag image tag`  | Rotula uma imagem (insere tag).                                       |
| `docker history image`  | Exibe o histórico de uma imagem.                                      |
| `docker inspect image`  | Exibe informações básicas (low-level information) de uma imagem.      |

# Comandos Run
A plataforma Docker utiliza o comando run (rodar) para criar containers a partir de imagens Docker. A sintaxe padrão para comandos dessa natureza está indicada abaixo:

docker run (options) image (command) (arg…)

Depois da sintaxe padrão, utilize uma das seguintes flags para rodar o comando:

| Flag                 | Explicação                                                             |
|-------------------------|-------------------------------------------------------------------------|
| `–detach , -d`          | Lista imagens.                                                        |
| `–env , -e`             | Remove uma imagem.                                                    |
| `–hostname , -h`  | Rotula uma imagem (insere tag).                                             |
| `–label , -l`  | Exibe o histórico de uma imagem.                                               |
| `–name`                 | Atribui um nome a um container                                        |
| `–network`              | Conecta um container a uma rede (network)                             |
| `–rm`                   | Remove um container quando ele é encerrado                            |
| `–read-only`            | Define o modo de “apenas leitura” para o sistema de arquivos do container (filesystem read-only) |
| `–workdir , -w`         | Configura um diretório de trabalho em um container.                   |

# Comandos de Registro
Caso você precise interagir com o Docker Hub, use alguns dos seguintes comandos:

| Comando                                                                                               | Explicação                                                                                               |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `docker login	`                                                                                       | Faz o login em um registro                                                                             |
| `docker logout`                                                                                       | Faz o logout de um registry                                                                            |
| `docker pull mysql`                                                                                   | Traz ou busca uma imagem de um registro (pull)                                                         |
| `docker push repo/ rhel-httpd:latest`                                                                 | Envia ou leva uma imagem a um registry (push)                                                          |
| `docker search term`                                                                                  | Faz uma pesquisa no Docker Hub em busca de imagens com o termo especificado (term)                     |

# Comandos de Serviço
Gerencie todos os serviços Docker com apenas alguns desses comandos básicos:

| Comando                                                                                               | Explicação                                                                                               |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `docker service ls`                                                                                   | Lista todos os serviços que estão rodando em um swarm                                                   |
| `docker stack services stackname`                                                                     | Lista todos os serviços que estão rodando                                                               |
| `docker service ps servicename`                                                                       | Lista a tarefa (task) de um serviço                                                                     |
| `docker service update servicename`                                                                   | Atualiza um serviço                                                                                     |
| `docker service create image`                                                                         | Cria um novo serviço                                                                                    |
| `docker service scale servicename=10`                                                                 | Dimensiona um ou mais serviços replicados                                                               |
| `docker service logs stackname servicename`                                                           | Lista todos os registros (logs) de serviços                                                             |  

# Comandos de Rede
Se você precisa interagir com a rede Docker, pode utilizar um comando de natureza “network”, como os apresentados a seguir:

| Comando                                                                                               | Explicação                                                                                               |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `docker network create networkname`                                                                   | Cria uma nova rede (new network)                                                                      |
| `docker network rm networkname`                                                                       | Remove uma rede específica                                                                            |
| `docker network ls`                                                                                   | Lista todas as redes                                                                                  |
| `docker network connect networkname container`                                                        | Conecta um container a uma rede                                                                       |
| `docker network disconnect networkname container`                                                     | Desconecta um container de uma rede                                                                   |
| `docker network inspect networkname`                                                                  | Exibe informações detalhadas sobre a rede (network)                                                   |     

