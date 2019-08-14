# init-cloud
Primeiros passos na configuração de um servidor na nuvem.

## Antes de começar
### O que é
- VPN
- VPS
- SSH

## Criando digital ocean
- Criando uma instancia na digital ocean

### Criando Droplet
Inicialmente temos as opções
- Distribuições
- Containers de distribuições
- Marketplace
- Backups
- Imagem customizada

Vamos escolher **distribuição** e ir para a **Ubuntu 16.04 X64**.

### Escolhendo plano
Tome cuidado com o plano, pois inicialmente ele inicia com um valor alto.

Vamos usar a do tipo **Standard**.

Depois a maquina de **$ 5/mo**.

### Adicionando backup
É recomendado usar o backup usado pela digital ocean, e nos ajuda realizando toda semana o backup da imagem.
> Isso tem o valor de 1 dolar por mes.

### Criando chave publica e adicionando SSH Key
Podemos adicionar uma chave agora na criação da maquina.

Vamos adicionar mais tarde uma chave na mão.

#### Vamos criar uma chave
```sh
ssh-keygen -r rsa
```

#### Adicionando chave
Vamos copiar a chave usando
```sh
cat ~/.ssh/id_rsa.pub
```

## SSH
### O que é
- O que é o Secure Shell (SSH)

### Instalação
- Instalando no Linux

### Configuração
- Retirando login senha
- Retirando login root
- Inserindo login por chave publica
- Perigos de logando por senha

## Node
### O que é
### Instalando no Linux
Aqui vai um exemplo de como podemos instalar a versão **LTS** do node para:
- Debian s2
- Ubuntu

```sh
# Using Ubuntu
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -sL https://deb.nodesource.com/setup_10.x | bash -
apt-get install -y nodejs
```
> Referencia: https://github.com/nodesource/distributions#deb



### Como usar
- NPM install
- NPM run
- NPM serve

## Mysql
### O que é
### Instalando
- Instalando no Linux

### Configurando
- Configurações de segurança
- Criação de banco
- Exportar/Importar DB
- Inserir na inicialização do sistema


## PM2
### O que é
### Instalando
- Instalando no Linux

### Configurando
- Subindo projeto
- Criando arquivo de configuração
- Verificar se mesmo o serviço caindo ele volte usando o resurrect

## NGINX
### O que é
### Instalando
- Instalando no Linux

### Configurando
- Criando proxy reverso
- Servindo site estático


## Resolvendo erros
- Reiniciar servidor
- Mostrar serviços que estão em funcionamento
- Inserindo serviço na inicialização do sistema
- Verificando logs
- Inserindo logs

## Firewall (UFW)

### O que é

### Instalando
- Instalando no Linux

### Configurando
- Verificando os perigos de usar sem firewall
- Cuidados a serem tomados
- Criando firewall
