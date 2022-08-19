
echo "Criando diretórios"


mkdir /publico
mkdir /adm
mkdir /ven
mkdir /sec

echo "Criando grupos de usuários"

groupadd GRP_ADM
groupadd GRP_VEN
groupadd GRP_SEC

echo "Criando usuários"

useradd carlos -c "Carlão" -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) 
useradd maria -c "Mariona" -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) 
useradd joão -c "Joaozin" -m -s /bin/bash -p $(openssl passwd -crypt S3nh4)
  
useradd debora -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) 
useradd sebastiao-m -s /bin/bash -p $(openssl passwd -crypt S3nh4) 
useradd roberto -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) 
 
useradd josefina -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) -G GRP_SEC
useradd amanda -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) -G GRP_SEC
useradd rogerio -m -s /bin/bash -p $(openssl passwd -crypt S3nh4) -G GRP_SEC

echo "Adicionando usuários ao grupos"

usermod GRP_ADM carlos
usermod GRP_ADM maria 
usermod GRP_ADM joao

usermod GRP_VEN debora 
usermod GRP_VEN sebastiao
usermod GRP_VEN roberto


echo "Criando permissões de diretórios"

chown root:GRP_ADM /adm
chown root:GRP_VEN /ven
chown root:GRP_SEC /sec

chmod 770 /adm
chmod 770 /ven
chmod 770 /sec
chmod 777 /publico

echo "Finalizado!"




