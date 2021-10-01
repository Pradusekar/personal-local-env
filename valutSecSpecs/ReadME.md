# Vault Setup

## Follow below steps

1. https://www.bogotobogo.com/DevOps/Docker/Docker-Vault-Consul.php
2. cd ~/Desktop/Vault-Consul-Docker
3. docker-compose up -d --build
4. docker exec -it 7810bffdb4c6 bash 
5. vault operator init
```
Unseal Key 1: GsBg9TloNXvfld/8qHmWlwrq2T0M1CXjnvN7U7/SxE8m
Unseal Key 2: oK8HcY4TVUKCNy86uds7h30dLK7ogfU/fVaZkrGTPDsB
Unseal Key 3: vQJG+2hxP+xwhg0xXRuIb3Jecwjs2OvQbMExnUpY8EFb
Unseal Key 4: hjJsSGgVyp5ZLRY+OwkmUzhFSjgePbE2GbzP02ctujJv
Unseal Key 5: frBxYyQsTggomxILF7KC+km62inqoeke94MvjdpYHjkb
```
Initial Root Token: 350b1061-e890-882b-df3b-27f400c7e0e3
6. vault operator unseal $token ( -use this command with 3 token to unlock root token)
7. vault login $ Root token (use root token)
```
token_accessor --> fd653514-d81b-e218-1b66-3000d345c3f5
```
8. vault audit enable file file_path=/vault/logs/audit.log
9. vault audit list
10. http://localhost:8200/ui/vault/secrets <--(UI for vault)
11. Request to create records 
```
curl \
>     -H "X-Vault-Token: $VAULT_TOKEN" \
>     -H "Content-Type: application/json" \
>     -X POST \
>     -d '{ "data": { "foo": "world" } }' \
>     http://127.0.0.1:8200/v1/secret/data/hello
```
12. Request to get record 
```
 curl \
>     -H "X-Vault-Token: $VAULT_TOKEN" \
>     -X GET \
>     http://127.0.0.1:8200/v1/secret/data/hello
```