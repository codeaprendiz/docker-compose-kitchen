# Let's Encrypt HTTP Challenge
[acme-http](https://docs.traefik.io/user-guides/docker-compose/acme-http/)

Steps

- Create a VM on any cloud provider (like google cloud)

![](../part1-letsEncrypt-tls-challenge/.ReadMe_images/vm-created-gc.png)

- Install docker-compose

- Create a DNS record like [here](https://www.noip.com/) and assing it to the public ip of the VM created.

![](.ReadMe_images/dns-record-created.png)

- Finally run the following command to start the containers

```bash
root@traefik-lets-encrypt:/home/ankit# docker-compose up -d
Creating network "ankit_default" with the default driver
Creating traefik        ... done
Creating simple-service ... done
```

- You can check the logs and verify if the cert is downloaded

```bash
$ docker logs traefik
...
time="2020-04-13T12:32:14Z" level=debug msg="No default certificate, generating one"
time="2020-04-13T12:32:15Z" level=debug msg="Try to challenge certificate for domain [httpacmetest.gotdns.ch] found in HostSNI rule" rule="Host(`httpacmetest.gotdns.ch`)" routerName=whoami@docker providerName=myresolver.acme
time="2020-04-13T12:32:15Z" level=debug msg="Looking for provided certificate(s) to validate [\"httpacmetest.gotdns.ch\"]..." providerName=myresolver.acme rule="Host(`httpacmetest.gotdns.ch`)" routerName=whoami@docker
time="2020-04-13T12:32:15Z" level=debug msg="Domains [\"httpacmetest.gotdns.ch\"] need ACME certificates generation for domains \"httpacmetest.gotdns.ch\"." rule="Host(`httpacmetest.gotdns.ch`)" routerName=whoami@docker providerName=myresolver.acme
time="2020-04-13T12:32:15Z" level=debug msg="Loading ACME certificates [httpacmetest.gotdns.ch]..." rule="Host(`httpacmetest.gotdns.ch`)" routerName=whoami@docker providerName=myresolver.acme
time="2020-04-13T12:32:17Z" level=debug msg="Building ACME client..." providerName=myresolver.acme
time="2020-04-13T12:32:17Z" level=debug msg="https://acme-v02.api.letsencrypt.org/directory" providerName=myresolver.acme
time="2020-04-13T12:32:17Z" level=info msg=Register... providerName=myresolver.acme
time="2020-04-13T12:32:17Z" level=debug msg="legolog: [INFO] acme: Registering account for ankit.codeaprendiz@gmail.com"
time="2020-04-13T12:32:17Z" level=debug msg="Using HTTP Challenge provider." providerName=myresolver.acme
time="2020-04-13T12:32:17Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] acme: Obtaining bundled SAN certificate"
time="2020-04-13T12:32:18Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] AuthURL: https://acme-v02.api.letsencrypt.org/acme/authz-v3/3934981712"
time="2020-04-13T12:32:18Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] acme: Could not find solver for: tls-alpn-01"
time="2020-04-13T12:32:18Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] acme: use http-01 solver"
time="2020-04-13T12:32:18Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] acme: Trying to solve HTTP-01"
time="2020-04-13T12:32:18Z" level=debug msg="Unable to split host and port: address httpacmetest.gotdns.ch: missing port in address. Fallback to request host." providerName=myresolver.acme
time="2020-04-13T12:32:18Z" level=debug msg="Retrieving the ACME challenge for token fvz8CGOqJfMQ9gNULRnvqfLQ0UuJu3FCvAXdqX4hy-A..." providerName=myresolver.acme
time="2020-04-13T12:32:18Z" level=debug msg="Unable to split host and port: address httpacmetest.gotdns.ch: missing port in address. Fallback to request host." providerName=myresolver.acme
time="2020-04-13T12:32:18Z" level=debug msg="Retrieving the ACME challenge for token fvz8CGOqJfMQ9gNULRnvqfLQ0UuJu3FCvAXdqX4hy-A..." providerName=myresolver.acme
time="2020-04-13T12:32:19Z" level=debug msg="Unable to split host and port: address httpacmetest.gotdns.ch: missing port in address. Fallback to request host." providerName=myresolver.acme
time="2020-04-13T12:32:19Z" level=debug msg="Retrieving the ACME challenge for token fvz8CGOqJfMQ9gNULRnvqfLQ0UuJu3FCvAXdqX4hy-A..." providerName=myresolver.acme
time="2020-04-13T12:32:19Z" level=debug msg="Unable to split host and port: address httpacmetest.gotdns.ch: missing port in address. Fallback to request host." providerName=myresolver.acme
time="2020-04-13T12:32:19Z" level=debug msg="Retrieving the ACME challenge for token fvz8CGOqJfMQ9gNULRnvqfLQ0UuJu3FCvAXdqX4hy-A..." providerName=myresolver.acme
time="2020-04-13T12:32:21Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] The server validated our request"
time="2020-04-13T12:32:21Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] acme: Validations succeeded; requesting certificates"
time="2020-04-13T12:32:25Z" level=debug msg="legolog: [INFO] [httpacmetest.gotdns.ch] Server responded with a certificate."
time="2020-04-13T12:32:25Z" level=debug msg="Certificates obtained for domains [httpacmetest.gotdns.ch]" routerName=whoami@docker providerName=myresolver.acme rule="Host(`httpacmetest.gotdns.ch`)"
time="2020-04-13T12:32:25Z" level=debug msg="Configuration received from provider myresolver.acme: {\"http\":{},\"tls\":{}}" providerName=myresolver.acme
time="2020-04-13T12:32:25Z" level=debug msg="Adding certificate for domain(s) httpacmetest.gotdns.ch"
...
```

- Also note that the following directory will be created after the execution of command
```bash
# ls
docker-compose.yaml  letsencrypt
# ls letsencrypt/
acme.json
# cat letsencrypt/acme.json | grep -A 5 "Certificates"
    "Certificates": [
      {
        "domain": {
          "main": "httpacmetest.gotdns.ch"
        },
        "certificate": "LS******** "...
...
```

- Now visit the domain to check if certificate is being generated

![](.ReadMe_images/browser-validation-of-cert.png)


- Now even if you remove the letsEncrypt/acme.json, it will get fetched again
```bash
root@traefik-lets-encrypt:/home/ankit# mv letsencrypt/acme.json /tmp
root@traefik-lets-encrypt:/home/ankit# ls letsencrypt/
root@traefik-lets-encrypt:/home/ankit# 
root@traefik-lets-encrypt:/home/ankit# docker stop traefik
traefik
root@traefik-lets-encrypt:/home/ankit# docker-compose up -d
simple-service is up-to-date
Starting traefik ... done
root@traefik-lets-encrypt:/home/ankit# ls
docker-compose.yaml  letsencrypt
root@traefik-lets-encrypt:/home/ankit# ls letsencrypt/
acme.json
```






