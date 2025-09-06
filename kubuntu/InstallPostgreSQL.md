# Install PostgreSQL on Ubuntu

## Method: Using the official apt repository

### 1. Update package list
```bash
sudo apt update
```

### 2. Install PostgreSQL
```bash
sudo apt install postgresql postgresql-contrib -y
```
- `postgresql` → Core database server  
- `postgresql-contrib` → Extra features and extensions (e.g., `uuid-ossp`, `pgcrypto`)

### 3. Check service status
```bash
systemctl status postgresql
```
If running, you should see `active (running)`.

Control commands:
```bash
sudo systemctl start postgresql
sudo systemctl stop postgresql
sudo systemctl restart postgresql
```

### 4. Switch to PostgreSQL superuser
```bash
sudo -i -u postgres
```
Enter the PostgreSQL interactive shell:
```bash
psql
```

### 5. Create a database and user
Inside `psql`:
```sql
-- Create a new user 'eric' with password
CREATE USER eric WITH PASSWORD 'mypassword';

-- Create a new database owned by 'eric'
CREATE DATABASE ericdb OWNER eric;

-- Grant privileges
GRANT ALL PRIVILEGES ON DATABASE ericdb TO eric;
```

Exit `psql`:
```sql
\q
```

### 6. Test the connection
```bash
psql -U eric -d ericdb -h 127.0.0.1 -W
```

---

## Optional: Enable remote connections

### 1. Edit `postgresql.conf`
```bash
sudo nano /etc/postgresql/16/main/postgresql.conf
```
Find and update:
```
listen_addresses = '*'
```

### 2. Edit `pg_hba.conf`
```bash
sudo nano /etc/postgresql/16/main/pg_hba.conf
```
Add the following line at the bottom:
```
host    all    all    0.0.0.0/0    md5
```

### 3. Restart service
```bash
sudo systemctl restart postgresql
```

