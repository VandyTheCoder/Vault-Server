# Vault Server
Welcome to the Docker Compose repository for running a Vault server! This repository provides a convenient way to deploy and manage a HashiCorp Vault server using Docker Compose.

## Introduction
Vault is a tool for managing secrets and protecting sensitive data. It provides a secure way to store, access, and manage tokens, passwords, certificates, and other secret data. This repository offers a Docker Compose setup to quickly spin up a Vault server instance for development, testing, or demonstration purposes.

## Prerequisites
To use this Docker Compose configuration, ensure you have the following software installed on your system:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Install Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started
1. Clone this repository to your local machine:
```sh
git clone https://github.com/VandyTheCoder/Vault-Server.git
cd Vault-Server
```

2. Configuration

The `config.hcl` file contains configuration that can be adjusted to configure the Vault server's behavior. Make sure to review and modify the variables according to your requirements before running the container.

3. Start Vault Server
```sh
docker-compose up -d
```
Expect output:
```
➜ Lucfier Revenant: docker-compose up -d
[+] Running 2/2
 ✔ Network vault_default  Created
 ✔ Container vault        Started 
```

4. Init Seal/Unseal Key for Vault
```sh
➜ Lucifer Revenant: docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                    NAMES
30678fd2ab54   vault:1.13.3   "docker-entrypoint.s…"   4 seconds ago   Up 3 seconds   0.0.0.0:8200->8200/tcp   vault

➜ Lucifer Revenant: docker exec -it 306 sh

/$: vault operator init -key-shares=3 -key-threshold=2

Unseal Key 1: O4c3NLADnmYOOOV9cnh2oj/9qeOOky049/VYaxgHe+v9
Unseal Key 2: C2bDJmlqinF7Jzf7O18kr1WUXCJfF2ar+Yg+5HikNKnY
Unseal Key 3: qbO8DditfmeO96LwyetlVHBTfcIooCgK4Lu+dyenGX/Q

Initial Root Token: hvs.qsBVVjsk2iEtYvQMnUi7vjRi

Vault initialized with 3 key shares and a key threshold of 2. Please securely
distribute the key shares printed above. When the Vault is re-sealed,
restarted, or stopped, you must supply at least 2 of these keys to unseal it
before it can start servicing requests.

Vault does not store the generated root key. Without at least 2 keys to
reconstruct the root key, Vault will remain permanently sealed!

It is possible to generate new unseal keys, provided you have a quorum of
existing unseal keys shares. See "vault operator rekey" for more information.

/$: exit
```

5. Accessing the Vault Server UI: once the Vault server is up and running, you can access the Vault UI by opening your web browser and navigating to: [http://localhost:8200](http://localhost:8200)

6. Unseal Vault: use the generated unseal key from the the step number 4 to unseal vault.

7. Authentication: use the generated root token to authenticate into vault server.

## Advance Options
For more advanced configuration and usage options, please refer to the official [Vault documentation](https://www.vaultproject.io/docs).

## References
- [Vault Documentation](https://www.vaultproject.io/docs)
- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose)

## License
This project is licensed under the [MIT License](LICENSE).

---
Feel free to contribute, open issues, or provide feedback if you find any issues with this repository. Happy secret managing with Vault! 🗝️🔐