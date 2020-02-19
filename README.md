OpenApi を試す
====

コンテナ起動。  
初回はビルドに20分くらいかかる。
```bash
cd docker
docker-compose.exe up -d --build
```


コンテナの中に入る
```bash
docker-compose exec tools bash
```

OASをYAMLからJSONに変換
```bash
cd /app/hoge
swagger-cli bundle -o fuga.json fuga.yml
```

# コード生成
## JS
ExpressでNodeJSのスタブサーバを作成
```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g nodejs-express-server \
   -o ../output/js/server
```

jsのクライアントライブラリを作成
```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g javascript \
   -o ../output/js/client
```

## PHP
```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php-laravel \
   -o ../output/php/server_laravel
```

```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php-lumen \
   -o ../output/php/server_lumen
```

```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php-slim4 \
   -o ../output/php/server_slim4
```

```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php-ze-ph \
   -o ../output/php/server_zendExpressive
```

```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php-symfony \
   -o ../output/php/server_symfony
```

```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar generate \
   -i fuga.yml \
   -g php \
   -o ../output/php/client
```

## その他
対応しているものの確認
```bash
java -jar /generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar list
```



# SwaggerUI と SwaggerEditor も

- [Swagger UI](http://localhost:9001)
- [Swagger Editor](http://localhost:9002)
