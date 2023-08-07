# Definição do Samba
O Samba é um software livre e de código aberto que oferece serviços de compartilhamento de arquivos e impressoras em redes que utilizam o protocolo SMB/CIFS (Server Message Block/Common Internet File System). Ele permite a interoperabilidade entre sistemas operacionais Windows, Linux/Unix e outros dispositivos de rede.

# As principais funções do Samba são:

Compartilhamento de Arquivos: O Samba permite que computadores em uma rede compartilhem pastas e arquivos entre si, possibilitando o acesso a esses recursos de forma semelhante a uma rede local Windows.

Compartilhamento de Impressoras: Além dos arquivos, o Samba também permite que impressoras conectadas a um computador sejam compartilhadas e acessadas por outros dispositivos da rede.

Integração com Domínios Windows: O Samba é capaz de atuar como um controlador de domínio em uma rede, permitindo a integração com sistemas Windows e a autenticação de usuários.

Compatibilidade com o Protocolo SMB/CIFS: O protocolo SMB/CIFS é amplamente utilizado em ambientes Windows, e o Samba possibilita que sistemas Linux e Unix se comuniquem e compartilhem recursos com máquinas Windows.
# Configuração do Samba
## Comandos:
### Atualizar a lista de pacotes disponíveis nos repositórios 
apt-get update
### Instalação
apt-get install samba 
![Instalação do samba](https://github.com/PolianaR/livro-gsi-2023-1/blob/ec34f251d62f2015fbbafac5b7828dcabb9a6cd1/instalacao%20do%20samba.jpg)
 ### Acessar o /etc/samba
 cd /etc/samba
### Mover o arquivo
 mv smb.conf smb.conf.bkp

### Para criar diretórios 
mkdir (caminho do diretório / nome do diretório)
ls -s (caminho) para validar
chmod 777 (caminho do diretório/ nome do diretório)
vim smb.conf
## Nome do compartilhamento
-comment = comentário quando coloca o mouse em cima da pasta compartilhada 
path = caminho da pasta
valid users = usuários válidos para acesso ao samba
$ salve o arquivo
## Criando usuário e transformando em usuário do samba
useradd ( nome do usuário)
- pdbedit -L #verificar usuários do samba
smbpasswd -a (nome do usuário) 
### Após o comando, será necessário colocar a senha para usuário acessar o compartilhamento.


## Reiniciando o serviço samba
systemctl restart smbd

## Verificar status do samba
systemctl status smbd
![Comando status do samba](https://github.com/PolianaR/livro-gsi-2023-1/blob/ea081e00baf94dbd745ee3477e61555b3e11aac1/status%20smbd.jpg)
## Compartilhamento
No linux após a configuração vai em Rede e digita o (ip  a)para acessar a rede de compartilhamento ou coloca o nome do servidor no meu caso maceio e posteriormente criei maragogi:
\\192.168.__.__
## Compartilhamento de pastas:
### O script será usado no power shell 
### Script:

### O caminho da importação: 
    Import-Csv -Path .\Desktop\alunos.csv -Delimiter ',' -PipelineVariable User | ForEach-Object -Process { #O caminho da importação:
    $password = -join ((65..90) + (97..122) + (48..57) | Get-Random -Count 20 |ForEach-Object -Process {[char]$_} )
    $securePassword = ConvertTo-SecureString -String $password -AsPlainText -Force
    #colunas que serão usadas do planilha $San = "{0}.{1}.{2}" -f $User.GivenName, $User.MiddleInitial, $User.Surname
    $SamAccountName = ([Text.Encoding]::ASCII.GetString([Text.Encoding]::GetEncoding("Cyrillic").GetBytes($San))).ToLower()
    ##Abaixo será descrito as colunas que será usadas
## Esse parâmetros são os que são pedidos na criação dos usuários
$NewAdUserParameters = @{
        GivenName = $User.GivenName
        Surname = $User.Surname
        DisplayName = ('{0} {1}' -f $User.GivenName, $User.Surname)
        Name = $SamAccountName
        Description = 'Usuário criado via Script'
        AccountPassword = $securePassword
        Department = $User.RH
}
   New-AdUser @NewAdUserParameters
}
 
