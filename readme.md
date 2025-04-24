
docker exec -it theband_dashboard superset fab create-admin \
              --username admin \
              --firstname Superset \
              --lastname Admin \
              --email admin@superset.com \
              --password admin

docker exec -it theband_dashboard superset db upgrade

docker exec -it theband_dashboard superset load_examples

docker exec -it theband_dashboard superset init

dremio+flight://paulossjunior:Forceknight2009!@dremio:32010/dremio?UseEncryption=false