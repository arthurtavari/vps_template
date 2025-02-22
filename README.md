## Passos de Instalação

1. Atualizar o sistema e instalar apparmor-utils:
   sudo apt-get update ; apt-get install -y apparmor-utils

2. Configurar o nome do host:
   hostnamectl set-hostname manager1

3. Alterar o localhost para `manager1` no arquivo `/etc/hosts`:
   - Edite o arquivo com o comando:
     nano /etc/hosts
   - Altere a linha para:
     127.0.0.1 manager1

4. Instalar o Docker:
   curl -fsSL https://get.docker.com | bash

5. Inicializar o Docker Swarm:
   docker swarm init

6. Criar rede overlay para o Docker:
   docker network create --driver=overlay network_public

7. Configurar e executar o Traefik:
   - Crie e edite o arquivo `traefik.yaml` com:
     nano traefik.yaml
   - Execute o comando:
     docker stack deploy --prune --resolve-image always -c traefik.yaml traefik

8. Instalar o Portainer:
   - Crie e edite o arquivo `portainer.yaml` com:
     nano portainer.yaml
   - Execute o comando:
     docker stack deploy --prune --resolve-image always -c portainer.yaml portainer