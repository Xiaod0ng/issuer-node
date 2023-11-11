# Running the system for the first time

1. Install git on linux system. I am using windows subsystem for linux (WSL) on windows 11.

2. Clone the repository

```bash
git clone https://github.com/Xiaod0ng/issuer-node
```

3. Update `ISSUER_ETHEREUM_URL` variable in .env-issuer

4. Follow [docker documentation](https://docs.docker.com/desktop/wsl/) to turn on Docker Desktop for WSL

5. Run `make up` in Linux terminal

6. Run the following command to set private key
```bash
make private_key=<YOUR_WALLET_PRIVATE_KEY> add-private-key;
```

7. Run the following command to add vault toekn to configuration file
```bash
make add-vault-token
```

8. Run the following command to generate a new issuer DID
```bash
make generate-issuer-did
```

9. Run `make run-ui` to start the webpage

# Not first time

If all variables are configured properly, you need to follow the steps below.

1. Start Docker Desktop

2. Start the public URL 

3. In Linux terminal, run `make up`

You should be able to navigate to the sites.

Possible Problems: