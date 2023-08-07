Interfaces, log, SSH e DHCP
Interfaces
Como listar: Para listar o etc/network/interfaces.d, primeiro eu acessei o arquivo (diretório) com o comando: /etc/network/interfaces.d e digitei o comando: ls.

Como configurar:
Use um editor de texto como o "vim" ou o "nano" para criar um novo arquivo de configuração na pasta "/etc/network/interfaces.d":

sudo vim /etc/network/interfaces.d/eth0

Arquivo /etc/network/interfaces.d/eth0
Texto no arquivo
auto eth0 iface eth0 inet static address 192.168.1.100 netmask 255.255.255.0 gateway 192.168.1.1

Salve o arquivo e feche o editor de texto.
Reinicie o serviço de rede para aplicar as alterações:
sudo systemctl restart networking

Como ativar/desativar: com os comandos ifup enp0s3 e ifdown enps0s3
Para ativar e desativar a interface de rede "enp0s3" usando os comandos ifup e ifdown, você precisa ter permissões de superusuário (root) para executar esses comandos. Abaixo estão as etapas para ativar e desativar a interface:

Para ativar a interface "enp0s3", use o comando ifup:
sudo ifup enp0s3

Para desativar a interface "enp0s3", use o comando ifdown:

sudo ifdown enp0s3
Lembre-se de que o nome da interface pode variar dependendo da sua distribuição Linux e da configuração específica do sistema. "enp0s3" é apenas um exemplo; a sua interface de rede pode ser chamada de forma diferente, como "eth0" ou "eno1". ara verificar o status das interfaces de rede, você pode usar o comando ifconfig ou o comando mais recente ip (a partir do pacote iproute2). Vou mostrar ambos os comandos:

Comando ifconfig:
ifconfig

Isso exibirá informações sobre todas as interfaces de rede ativas no seu sistema.

Comando ip:
sql

Este comando também exibirá informações detalhadas sobre todas as interfaces de rede ativas:
ip addr show

Abra o arquivo de configuração da interface "enp0s3" para edição (você precisará de permissões de superusuário):
sudo nano /etc/network/interfaces.d/enp0s3

Adicione ou verifique as configurações para configurar o endereço IP estático, gateway e máscara de rede:
Configuração da interface enp0s3
auto enp0s3 iface enp0s3 inet static address SEU_ENDERECO_IP netmask SUA_MASCARA_DE_REDE gateway SEU_GATEWAY

Substitua "SEU_ENDERECO_IP", "SUA_MASCARA_DE_REDE" e "SEU_GATEWAY" pelos valores corretos para a sua rede. Por exemplo:

css

address 192.168.1.100 netmask 255.255.255.0 gateway 192.168.1.1 dns-nameservers 10.214.0.10 10.22.0.10

Isso define os servidores DNS para "10.214.0.10" e "10.22.0.10", conforme mencionado na sua pergunta.

Salve o arquivo e feche o editor de texto.

Reinicie o serviço de rede para aplicar as alterações:
sudo systemctl restart networking

Isso configura o endereço IP estático, gateway e servidores DNS para a interface "enp0s3". Certifique-se de substituir os valores corretos pelos da sua rede. Após reiniciar o serviço de rede, as novas configurações entrarão em vigor.
Interfaces comandos feitos

livro-gsi-2023-1/docs/interfaces.md at main · PolianaR/livro-gsi-2023-1
