# Microsoft SQL Server on Docker

Docker Compose environment running **Microsoft SQL Server 2022 Developer Edition**, configured for **SQL Server Management Studio**.

Can be ran/accessed locally or via network.

---

## 1. Connection Details for SSMS

| Setting | Value |
| :--- | :--- |
| **Server type** | Database Engine |
| **Server name** | `ipaddress,1433` |
| **Authentication** | **SQL Server Authentication** |
| **Login** | `sa` |
| **Password** | *(value in `.env`)* |

Enable **trust server certificate** in the connection properties tab.

--

## 2. Directory Structure
```text
/Projects/server/
├── docker-compose.yml   
├── .env                 
├── .env.example         # Template for environment configuration
├── .gitignore           # Ignores env and backups
├── backup/             
└── readme.md            
```
---

## 3. Managing the Server
Run these commands from `/Projects/server`:

### Start the Server
```bash
docker compose up -d
```

### Stop the Server
```bash
docker compose down
```

### View Live Logs
```bash
docker compose logs -f
```

### Check Container Status
```bash
docker compose ps
```
---



## 5. Backups and Restores

Any file placed inside `./backup` on your host can be accessed


   ```sql
   RESTORE DATABASE [YourDatabase]
   FROM DISK = N'/var/opt/mssql/backup/your-database.bak'
   WITH MOVE 'YourDataLogicalName' TO '/var/opt/mssql/data/YourDatabase.mdf',
        MOVE 'YourLogLogicalName'  TO '/var/opt/mssql/log/YourDatabase_log.ldf';
   ```
