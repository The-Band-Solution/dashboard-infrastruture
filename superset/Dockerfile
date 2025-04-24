FROM apache/superset
# Switching to root to install the required packages
USER root
# Example: installing the MySQL driver to connect to the metadata database
# if you prefer Postgres, you may want to use `psycopg2-binary` instead

# Example: installing a driver to connect to Redshift
# Find which driver you need based on the analytics database
# you want to connect to here:
# https://superset.apache.org/installation.html#database-dependencies
RUN pip install sqlalchemy-dremio

COPY arrow-flight-sql-odbc-driver-0.9.1.168-1.x86_64.rpm /tmp/

# Instale o driver Arrow Flight SQL ODBC usando alien
RUN apt-get update && apt-get install -y alien unixodbc && \
    alien -i /tmp/arrow-flight-sql-odbc-driver-0.9.1.168-1.x86_64.rpm && \
    rm /tmp/arrow-flight-sql-odbc-driver-0.9.1.168-1.x86_64.rpm



# Switching back to using the `superset` user
USER superset