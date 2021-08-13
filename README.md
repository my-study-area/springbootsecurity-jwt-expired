# springbootsecurity-jwt-expired
<p>
    <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/my-study-area/springbootsecurity-jwt-expired">
    <a href="https://github.com/my-study-area">
        <img alt="Made by" src="https://img.shields.io/badge/made%20by-adriano%20avelino-gree">
    </a>
    <img alt="Repository size" src="https://img.shields.io/github/repo-size/my-study-area/springbootsecurity-jwt-expired">
    <a href="https://github.com/EliasGcf/readme-template/commits/master">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/my-study-area/springbootsecurity-jwt-expired">
    </a>
</p>

Implementação de Spring Boot + Spring Security + JSON Web Token exibindo mensagem de erro para token expirado.

Toda a aplicação foi desenvolvido com base no post [Implement Spring Boot + JSON Web Token Security](https://www.javainuse.com/webseries/spring-security-jwt/chap4)

Os arquivos alterados para permitir a exibição de mensagem de erro para token expirado pode ser acompanhada no commit [34b6aae](https://github.com/my-study-area/springbootsecurity-jwt-expired/commit/34b6aae).

## Tecnologias
- Spring Boot
- Spring Security
- JWT

> Obs: não é utilizado banco de dados. Os usuários e senhas estão estáticos na classe [ src/main/java/com/javainuse/springbootsecurity/config/CustomUserDetailsService.java ](https://github.com/my-study-area/springbootsecurity-jwt-expired/blob/115dc06e02326d7ad371b5e23e0082693004e983/src/main/java/com/javainuse/springbootsecurity/config/CustomUserDetailsService.java)

## Inicialização da aplicação
```bash
#clona o projeto
git clone https://github.com/my-study-area/springbootsecurity-jwt-expired.git

#entra no diretório da plaicação
cd springbootsecurity-jwt-expired

#inicia a aplicação
./mvnw spring-boot:run
```

## Testes Manuais
>Obs: os tokens expiram em 30 segudos para facilitar os testes com token expirados.

Usuários e senhas para testes:

|Usuário|Senha|
|-------|-----|
|user   |user |
|admin  |admin|


Exemplo de requisição `POST` para gerar o token:
```bash
curl --location --request POST 'http://localhost:8080/authenticate' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "admin",
    "password": "admin"
}'
```
Resposta:
```json
{
  "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImlzQWRtaW4iOnRydWUsImV4cCI6MTYyODgwOTYwNCwiaWF0IjoxNjI4ODA5NTc0fQ.wkFlnn9HxDDWaVWJxxEPvqqJYvRY2GGtBptGc1HVR5A6Fm1SL1s2GZCYnm0hGqq1knYZYNdGiaj_PISCYxuH1w"
}
```

Exemplo de requisição `GET` (não se esqueça de alterar **seuToken** pelo token gerado na requisição acima):
```bash
curl --location --request GET 'http://localhost:8080/hellouser' \
--header 'Authorization: Bearer seuToken'
```
Resposta:
```json
Hello User
```
