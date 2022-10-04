# Traefik v2 HTTPS (SSL) on localhost


Clone this repo.


Next, go to the root of the repo and generate certificates using [mkcert](https://github.com/FiloSottile/mkcert) :

```bash
# If it's the firt install of mkcert, run
mkcert -install

# Generate certificate for domain "docker.localhost", "domain.local" and their sub-domains
mkcert -cert-file certs/local-cert.pem -key-file certs/local-key.pem "docker.localhost" "*.docker.localhost" "domain.local" "*.domain.local"
```


Create networks that will be used by Traefik:

```bash
docker network create traefik
``` 


Now, start containers with : 

```bash
# Start Traefik
docker-compose up -d
# Start "whoami-https" example
docker-compose -f whoami-https.yml up
# or "whoami-http" example
docker-compose -f whoami-http.yml up
```

You can now go to your browser at HTTPS [whoami-https.docker.localhost](https://whoami-https.docker.localhost),
or ar HTTP [whoami.docker.localhost](http://whoami.docker.localhost)

*Note: see .env for variables*

*Note: you can access to Træfik dashboard at: [traefik.docker.localhost](https://traefik.docker.localhost)*


