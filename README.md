# init-cloud
Primeiros passos na configuração de um servidor na nuvem.

## Antes de começar
### O que é
- VPS (Virtual Private Server)
- SSH (Secure Shell)

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

> Vamos adicionar mais tarde uma chave de forma manualmente.

#### Vamos criar uma chave
```sh
ssh-keygen -r rsa
```

#### Adicionando chave
Vamos copiar a chave usando179.80.189.242
```sh
cat ~/.ssh/id_rsa.pub
```

## SSH
### O que é
- O que é o Secure Shell (SSH)

### Instalação
- Instalando no Linux

Veja como podemos instalar o openssh client
```sh
sudo apt-get install openssh-client
```

### Configuração
- Retirando login senha
- Retirando login root
- Inserindo login por chave publica
- Perigos de logando por senha

## Node
### O que é
Node.js é uma plataforma construída sobre o motor JavaScript do Google Chrome para facilmente construir aplicações de rede rápidas e escaláveis. Node.js usa um modelo de I/O direcionada a evento não bloqueante que o torna leve e eficiente, ideal para aplicações em tempo real com troca intensa de dados através de dispositivos distribuídos.

> http://nodebr.com/o-que-e-node-js/

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
> Costumamos usar ele para instalar os requisitos ou uma biblioteca especifica

- NPM run
> Usamos ele para executar algo, um exemplo é o **npm run build**.

- NPM serve
> Podemos usar o **npm serve** para servir uma aplicação.

## Mysql
### O que é
O MySQL é um sistema de gerenciamento de banco de dados, que utiliza a linguagem SQL como interface. É atualmente um dos sistemas de gerenciamento de bancos de dados mais populares da Oracle Corporation, com mais de 10 milhões de instalações pelo mundo.

### Instalando
- Instalando no Linux

Podemos instalar o **mysql-server** da seguinte forma
```sh
apt-get install mysql-server
```

> Mas podemos encontrar
mysql-server - MySQL database server (metapackage depending on the latest version)
mysql-server-5.7 - MySQL database server binaries and system database setup
mysql-server-core-5.7 - MySQL database server binaries

### Configurando
- Configurações de segurança
```sh
# Criando usario
CREATE USER 'novousuario'@'localhost' IDENTIFIED BY 'password';
# Dando permissão ao usuario
GRANT ALL PRIVILEGES ON * . * TO 'novousuario'@'localhost';
```

- Criação de banco
> Podemos entrar no banco com o nosso usuario criado anteriormente é realizar
```sh
create database nome;
```

- Exportar/Importar DB
```sh
# Exportar
mysqldump -uroot -p nome_do_banco > /home/bkp.database.db

# Importar
mysql -uroot -p
mysql> source /home/bkp.database.db
```

## PM2
### O que é
O PM2 é um gerenciador de processos para o tempo de execução do JavaScript Node.js. Usamos ele para gerenciar nossas aplicações e assim servindo nosso projeto.

### Instalando
- Instalando no Linux
```sh
npm install pm2@latest -g
```

### Configurando
```sh
# configura o pm2 para inicializar com o sistema operacional.
pm2 startup
```

- Subindo projeto
```sh
# No -i, é possível delimitar o número de CPUs usadas
pm2 start app.js -i 1
```

- Criando arquivo de configuração
```sh
#Depois de iniciar todos os aplicativos que você deseja gerenciar, salve a lista que deseja recuperar na reinicialização da máquina com:
pm2 save
```

- Verificar se mesmo o serviço caindo ele volte usando o resurrect
```sh
# Ressuscitar manualmente os processos
# Isso traz de volta processos salvos anteriormente (via pm2 save):
pm2 resurrect
```

## NGINX
### O que é
Nginx (lê-se "engine x") é um servidor HTTP e proxy reverso, bem como um servidor para proxy de email IMAP/POP3, escrito por Igor Sysoev desde 2005.

O Nginx é um servidor web rápido, leve, e com inúmeras possibilidades de configuração para melhor performance.

### Instalando
- Instalando no Linux
```sh
apt-get install nginx
```

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
Um firewall tem como objetivo nos auxiliar na segurança de uma rede de computadores usando políticas de segurança a um determinado ponto da rede. O firewall pode ser do tipo filtros de pacotes, proxy de aplicações, etc. Os firewalls são geralmente associados a redes TCP/IP.

### Instalando
- Instalando no Linux
```sh
apt-get install ufw
```

### Configurando
- Verificando os perigos de usar sem firewall
> Uma porta exporta pode ser um problema pois pessoas podem acabar tentando acesso um serviço, por exemplo o mysql.

- Cuidados a serem tomados
> É recomendado que apenas as portas **22** (mesmo assim é recomendado estar usando uma VPN),**80** (HTTP), **443** (HTTPS).

- Criando firewall
> Criando firewall para a porta 3306 **mysql**.
```sh
ufw enable
ufw deny 3306
```
