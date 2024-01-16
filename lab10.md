# Laboratorio 10: Elasticsearch

## 1. Preparar el entorno

### Crear un indice llamado "bank" e importar el accounts.json: 
#### El _bulk se pone para poder pasar todos los documentos (filas) de los datos, si no lo pones solo conseguiras pasar la primera fila) El pretty y refresh se usan para refrescar el indie y proporcionar una respuesta formateada de manera legible.

```bash
curl -H "Content-Type: application/json" -XPOST "localhost:9200/bank/_bulk?pretty&refresh" --data-binary "@accounts.json"
```

### Comprobar que se ha importado correctamente (para poder ver toda la estructura)

```bash
curl -XGET "localhost:9200/bank/_search?pretty"
```

## Paginación (Obtener los resultados agrupados): --> por ejemplo, para recuperar los resultados de búsqueda en bloques y después mostrarlos de forma "bonita".

### Recuperar los 20 primeros documentos del indice "bank": 

```bash
curl -XGET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "size": 20
}
'
```
### Recuperar los segundos 20 documentos del indice "bank": 

```bash
curl -XGET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "size": 20,
  "from": 20
}
'
```

### Buscar los datos de las personas que residen en Texas (codigo de estado "TXT") y devolver los primeros 15 resultados.

```bash
curl -XGET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match": { "state": "TX" } },
  "size": 15
}
'
```

## Ordenación: Para poder mostrar los datos ordenados segun los criterios que quieras


