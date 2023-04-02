#!/bin/bash

# Criação dos diretórios dos departamentos
mkdir /publico /adm /ven /sec

# Criação dos grupos
groupadd GRP_ADM
groupadd GRP_VEN
groupadd GRP_SEC

# Criação dos usuários
useradd -m -d /home/carlos -s /bin/bash carlos
useradd -m -d /home/maria -s /bin/bash maria
useradd -m -d /home/joao -s /bin/bash joao
useradd -m -d /home/debora -s /bin/bash debora
useradd -m -d /home/sebastiana -s /bin/bash sebastiana
useradd -m -d /home/roberto -s /bin/bash roberto
useradd -m -d /home/josefina -s /bin/bash josefina
useradd -m -d /home/amanda -s /bin/bash amanda
useradd -m -d /home/rogerio -s /bin/bash rogerio

# Adiciona usuários aos grupos correspondentes
usermod -a -G GRP_ADM carlos
usermod -a -G GRP_VEN maria
usermod -a -G GRP_VEN joao
usermod -a -G GRP_SEC debora
usermod -a -G GRP_SEC sebastiana
usermod -a -G GRP_ADM roberto
usermod -a -G GRP_ADM josefina
usermod -a -G GRP_VEN amanda
usermod -a -G GRP_SEC rogerio

# Ajusta as permissões do diretório /publico para dar permissão total para todos os usuários
chmod -R 777 /publico

# Remove as permissões de leitura, escrita e execução para o grupo e outros nos diretórios dos departamentos
chmod -R g-rwx,o-rwx /adm
chmod -R g-rwx,o-rwx /ven
chmod -R g-rwx,o-rwx /sec

# Define o proprietário dos diretórios como root
chown -R root:root /publico /adm /ven /sec
