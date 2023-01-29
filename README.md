# POC-VAULT-NODEJS

This project guide covers the steps required to install and configure a single HashiCorp Vault container as defined in the Vault Reference Architecture and a example with nodejs application. Although not a strict requirement to follow the Vault Reference Architecture.


## Commands

```bash
docker run --name vault -p 8200:8200 vault:1.7.3

mkdir poc-vault-nodejs
cd poc-vault-nodejs
docker run --name vault -p 8200:8200 vault:1.7.3
docker exec -it vault /bin/sh
docker exec -it vault /bin/sh
npm install node-vault\n


vault write auth/approle/role/node-app-role \
    token_ttl=1h \
    token_max_ttl=4h \
    token_policies=readonly-kv-backend
    \

vault read auth/approle/role/node-app-role/role-id


vault write -f auth/approle/role/node-app-role/secret-id


vault kv put secret/mysql/webapp db_name="users" username="admin" password="passw0rd"

vault kv put secret/<path> db_name="users" username="admin" password="passw0rd"

export ROLE_ID=""
export SECRET_ID=""


path "secret/data/<path>" {
  capabilities = [ "read" ]
}
```