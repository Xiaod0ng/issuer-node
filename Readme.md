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

# Not the first time

## Remove services and start again

1. Run `make down` to remove existing services

2. Run `make up` to start the services

3. Run `make delete-did` to remove current DID

4. Delete the value of ISSUER_API_UI_ISSUER_DID in .env-api

5. Run `make generate-issuer-did` to generate a new issuer DID

6. Run `make run` to start API

7. Run `make run-ui` to start UI

8. Open Ngrok terminal, run `ngrok http --domain usefully-blessed-sunbird.ngrok-free.app 8088 --response-header-add "Access-Control-Allow-Origin: *"` to start the tunnel.

It may return ERR_NGROK_3200 error, please close the terminal, then repeat step 8.

## Resume from last time

If all variables are configured properly, you need to follow the steps below.

1. Start Docker Desktop

2. Go to the issuer-node folder, run `docker rm issuer-ui-1` to remove the image first, then run `make restart-ui` to start the ui again. This is caused by the issue illustrated [here](https://github.com/0xPolygonID/issuer-node/pull/542). 

3. Start the ngrok public tunnel

You should be able to navigate to the sites.


# Possible Problems

1. Network error after starting UI

Usually because there are docker images not running. Make sure `make run` is executed before `make run-ui` so that the API image is properly initiated. Check docker logs for more information.

