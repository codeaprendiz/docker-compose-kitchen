

To test the certificates are working

- nslookup to domain
```bash
$ nslookup server.domain.com
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   server.domain.com
Address: 23.12.43.56
```

- Login to the server  23.12.43.56. Assuming the certificates and key are valid for `*.domain.com`

```bash
$ docker-compose up -d
```



- Visit `https://server.domain.com/` on browser and validate if its being loaded
