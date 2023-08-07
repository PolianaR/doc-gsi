# SSH

## SSH
Atualizar a lista de pacotes disponíveis para garantir que você obtenha a versão mais recente do pacote:

sql

sudo apt update

## Instale o servidor SSH (OpenSSH Server) usando o comando apt:

sudo apt install openssh-server

## Para transferir uma pasta usando o comando SCP (Secure Copy) do Linux da origem para o destino, você pode usar a seguinte sintaxe:

scp -r origem pasta_de_destino

A opção "-r" indica que o comando SCP deve copiar de forma recursiva (ou seja, incluindo subpastas e arquivos dentro da pasta).

Supondo que você deseja transferir uma pasta chamada "meu_diretorio" localizada na origem "usuario@endereco_do_servidor:/caminho/para/pasta/meu_diretorio" para a pasta "/caminho/para/pasta_de_destino/" no destino, você pode usar o seguinte comando:

scp -r usuario@endereco_do_servidor:/caminho/para/pasta/meu_diretorio /caminho/

![Imagem do SSH ](https://github.com/PolianaR/livro-gsi-2023-1/blob/8a9483c96543ef2f6479564e33adacc6feed60c7/print%20ssh.png)
