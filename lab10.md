# Laboratorio 10: Elasticsearch

## Preparar el entorno

### Crear un indice llamado "bank" e importar el accounts.json: 

curl -H "Content-Type: application/json" -XPOST "localhost:9200/bank/_bulk?pretty&refresh" --data-binary "@accounts.json"

