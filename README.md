# 📊 TheBand Dashboard with Apache Superset and Dremio

This project sets up an **Apache Superset** instance in Docker with an example dashboard and a connection to **Dremio** using the Flight SQL protocol.

## 🚀 Quickstart

### 1. ✅ Create an Admin User

Run the following command to create an initial admin user for Superset:

```bash
docker exec -it theband_dashboard superset fab create-admin \
    --username admin \
    --firstname Superset \
    --lastname Admin \
    --email admin@superset.com \
    --password admin
```

### 2. 📦 Upgrade the Superset Database

Initialize and upgrade the internal metadata database:

```bash
docker exec -it theband_dashboard superset db upgrade
```

### 3. 🎓 Load Example Dashboards

Optional: Load sample dashboards and datasets:

```bash
docker exec -it theband_dashboard superset load_examples
```

### 4. ⚙️ Final Superset Initialization

Run Superset initialization routines:

```bash
docker exec -it theband_dashboard superset init
```

## 🔗 Connecting Superset to Dremio

To connect Superset to a Dremio instance, use the following **SQLAlchemy URI** format:

```
dremio+flight://<user>:<password>@dremio:32010/dremio?UseEncryption=false
```

- **Username**: `user`
- **Password**: `password`
- **Host**: `dremio`
- **Port**: `32010`
- **Database**: `dremio`
- **Encryption**: Disabled

> ⚠️ **Important:** Make sure to store your credentials securely and avoid committing them to version control.

### ✅ Supported Drivers

This connection assumes you have the **[Apache Superset Dremio Flight SQL plugin](https://github.com/dremio-hub/superset-dremio-flight-sql)** installed.

If not, install it with:

```bash
pip install sqlalchemy-dremio-flight
```

(If you're using a custom Docker image, you may need to add this to your image build.)

---

## 🐳 Environment

Make sure the Docker container `theband_dashboard` is running. If you're using `docker-compose`, your service might be defined like this:

```yaml
services:
  superset:
    container_name: theband_dashboard
    image: apache/superset:latest
    ports:
      - "8088:8088"
    ...
```

---

## 📚 Resources

- [Apache Superset Documentation](https://superset.apache.org/docs/)
- [Dremio Documentation](https://docs.dremio.com/)
- [Dremio Flight SQL SQLAlchemy Dialect](https://github.com/dremio-hub/superset-dremio-flight-sql)
