### To test custom TLS certs with docker-caddy

- Suppose we have the certs for custom domain `*.domain.com` and the certs are saved at the location `certs`
```bash
$ ls certs          
star_domain.com.key         star_domain_com.chained.crt 
```

- Ensure that we have the following entry is added to `/etc/hosts` file. As we will test the TLS certs for this domain.
```bash
$ cat /etc/hosts | grep cert-validation
127.0.0.1 cert-validation-srv.domain.com
``` 

- Start the docker caddy
```bash
docker-compose up
```

- Since there is automatic redirect from http to https we will see the following observations
```bash
$ curl  http://cert-validation-srv.domain.com 

$ curl -L http://cert-validation-srv.domain.com
hello world
$ curl https://cert-validation-srv.domain.com
hello world
```

- You can generate the password using the playbook. You have to put this password in Caddy file.  [Reference](https://caddyserver.com/docs/caddyfile/directives/basicauth)
```bash
$ ansible-playbook password-generation.yml -v
ok: [localhost] => {
    "msg": "JDJiJDEyJGRrWnExWmJGbnp0b3BoZmVjSVRnNk9TZXZ3T3VLNTFHUS9nRGs4a00yZ0lZQTZrSUR6MDUy"
}
```

