**Setup:**
1. `git clone git@github.com:kulybaba/laravel-docker.git`
2. `docker compose up -d`
3. `docker compose exec app sh -c 'composer create-project laravel/laravel .'`
4. `docker compose exec app sh -c 'chown -R www-data:www-data /home/www/'`

5.  Create index:
```shell
curl -X PUT 'localhost:9200/visit_ukraine/?pretty' -H 'Content-Type: application/json' -d '
{
    "mappings": {
        "properties": {
            "name": {"type": "text"},
            "age": {"type": "integer"},
            "phone": {"type": "text"}
        }
    }
}'
```

6. Create document:
```shell
curl -X POST 'localhost:9200/visit_ukraine/_doc/?pretty' -H 'Content-Type: application/json' -d '
{
    "name": "Peter",
    "age": 28,
    "phone": "+380960000000"
}'
```

7. Get documents from index:
```shell
curl -X GET 'localhost:9200/visit_ukraine/_search?pretty'
```

**Check DB connection:**
1. `docker compose exec app sh -c 'php artisan migrate:status'`
2. `docker compose exec app sh -c 'php artisan migrate'`

**Laravel project:** http://localhost:7777

**Elasticsearch:** http://localhost:9200

**Kibana:** http://localhost:5601

**View index:** https://allowing-blindly-gobbler.ngrok-free.app/goto/7c4bf380-0c3f-11ef-9d11-91447f9c951c