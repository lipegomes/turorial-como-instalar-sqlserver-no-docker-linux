# **Tutorial de configuração para desenvolver com SQL Server 2019 no Linux utilizando docker**

Este tutorial foi produzido por mim com intuito de ajudar as pessoas que estão iniciando no mundo de desenvolvimento a fim de aprender a configurar SQL Server 2019 em um container docker em um ambiente de desenvolvimento Linux.

## **1 - Instalação e Configuração do SQL Server 2019 no Linux**

Para instalação do docker em sua distribuição linux consulte a documentação oficial no link abaixo:

https://docs.docker.com/engine/install/

**Criar container docker do sqlserver 2019:**

```bash
sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=SuaSenha123#%" -p 1433:1433 \ 
--name SqlServer2019 -dit mcr.microsoft.com/mssql/server:2019-latest
```

**Verificar se o SqlServer 2019 foi instalado no docker:**

```bash
docker ps -a
```

**Executar o container com o SqlServer 2019:**

```bash
docker exec -it SqlServer2019 bash
```

**Acessar o banco de dados:**

```bash
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'SuaSenha123#%'
```

**Parar o  funcionamento do container:**

```bash
docker stop SqlServer2019
```

**Iniciar o container:**

```bash
docker start SqlServer2019
```



## **2 - Conectar e acessar o banco de dados pelo DBeaver:**

Para download do DBeaver acesse o link abaixo:

https://dbeaver.io/download/

- Ir em: Database > New Database Connection
- Conforme imagem abaixo, clique no icone do SQL Server e depois clique em next( botãoo na parte inferior).

![image-20210710191115740](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191115740.png)

- Confome imagem abaixo, use os seguintes valores:

  - Host: localhost
  - Database/Schema: master
  - Authentication: SQL Server Authentication (necessário para poder usar os valores de User e Password definidos durante a instalação do container do docker localmente).
  - User name(definido durante a instalação do container): sa
  - Password(definido durante a instalação do container): SuaSenha123#%

  ![image-20210710191306690](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191306690.png)

  - Clique em Test Connection para verificar se a configuração está correta e realizar uma conecção com sucesso.

    ![image-20210710191316076](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191316076.png)

    

- Agora o SQL Server 2019 está configurado no DBeaver para uso no Linux conforme imagem abaixo:

  ![image-20210710191354036](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191354036.png)



## **3 - Conectar e acessar o banco de dados utilizando o Azure Data Studio**

Para download do Azure Data Studio acesse o link abaixo:

https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15

- Clique em Create a connection

  ![image-20210710191413103](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191413103.png)

  

- Ao abrir a janela abaixo, utilize as configurações setadas durante a instalação do container conforme imagem abaixo e clique em Connect:

  - Connection type: Microsoft SQL Server
  - Server: localhost
  - Authentication type: SQL Login
  - User name: sa
  - Password: SuaSenha123#%
  - Database: <default>
  - Server group: <default>

  ![image-20210710191422520](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191422520.png)

  

- Após se conectar terá acesso ao banco de dados conforme imagem abaixo:

  ![image-20210710191429603](https://github.com/lipegomes/turorial-como-instalar-sqlserver-no-docker-linux/blob/main/assets/img/image-20210710191429603.png)
  
  Tenha um ótimo proveito desse tutorial, foi feito com simplicidade mas com intuito de ajudar e transmitir conhecimento.