# goexpert-rate-limiter
Resposta ao desafio técnico Rate Limiter da pós Go Expert.

Para iniciar o banco de dados Redis, execute o seguinte comando:
```shell
docker-compose up -d
```

Para iniciar o servidor da aplicação, navegue até a pasta ```server``` e execute:
```shell
go run main.go
```

Para executar os testes unitários da aplicação, navegue até a pasta ```server``` e execute:
```shell
go test -v
```

O arquivo ```.env```, localizado na pasta ```server```, contém as variáveis de ambiente necessárias para a execução da aplicação:

```
TOKEN_NAME=Nome do token a ser passado no cabeçalho da requisição
REQUEST_LIMIT_TOKEN=Limite de requisições com o token
REQUEST_LIMIT_IP=Limite de requisições por IP
BLOCK_TIME_TOKEN=Tempo de bloqueio do token
BLOCK_TIME_IP=Tempo de bloqueio do IP
DATABASE_URL=Endereço do servidor Redis disponibilizado pelo docker-compose
```

Para fazer uma requisição simples, utilize o comando:
```shell
curl http://localhost:8080
```

Para fazer uma requisição com um token válido (onde o valor de ```API_KEY``` corresponde ao valor da propriedade ```TOKEN_NAME``` no arquivo ```.env```), utilize o comando:
```shell
curl -H "API_KEY:abc123" http://localhost:8080/
```

Da mesma forma, para fazer uma requisição com um token inválido (onde o valor de ```API_KEY``` é diferente do valor da propriedade ```TOKEN_NAME``` no arquivo ```.env```) utilize o comando:
```shell
curl -H "API_KEY:invalidHeader" http://localhost:8080/
```
