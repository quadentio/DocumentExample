1. Tạo container MSSQL bằng docker

- Cách 1:
docker volume create --name vmssql --opt device=<hostpath> 
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Password123" -p 1533:1433 --name c-mssql --hostname h-mssql -d -v vmssql:/var/opt/mssql mcr.microsoft.com/mssql/server:2022-latest

- Cách 2:
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Password123" \
   -p 1533:1433 --name c-mssql --hostname h-mssql \
   -d \
   -v <hostpath>:/var/opt/mssql
   mcr.microsoft.com/mssql/server:2022-latest

# MSSQL
- image: mcr.microsoft.com/mssql/server:2022-latest
- user quan tri: `sa`
- port: `1433`
- database: `/var/opt/mssql`
- `-e SA_PASSWORD=Password789`
- `-e ACCEPT_EULA=Y`

# SQLCMD
- sqlcmd (/opt/mssql-tools/bin/sqlcmd)
- `sqlcmd -S host -U user -P password`

# yml file
- Copy content before:
  
version: "3"

services:
  huycq-mssql:
    image: "mcr.microsoft.com/mssql/server:2022-latest"
    container_name: mssqlserver         # tên container
    restart: always
    hostname: mssql
    environment:
      SA_PASSWORD: <YourPassword>          #Thiết lập password
      ACCEPT_EULA: Y
      # Express:

    volumes:
      - mssqlvolume:/var/opt/mssql/data # thư mục lưu DB
      - ./bk:/var/opt/mssql/backup      # thư  mục chứa file backup
    ports:
      - "1533:1433"                     # cổng kết nối

volumes:
    mssqlvolume:<hostpath>