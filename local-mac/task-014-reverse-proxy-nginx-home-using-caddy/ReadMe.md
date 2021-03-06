### We will try to understand how reverse proxy works.

- Nginx is running using docker-compose on container port 80 attached host port 8080 in network name 'host'
- Caddy is running using docker-compose port 80:80, 443:443 on the same network.
- Nginx home is serving "hello world from nginx"
- Caddy home is serving "hello world from caddy"
- Now when we hit [test.domain.com](test.domain.com) we would receive "hello world from nginx" by using reverse proxy. See caddy file for more details.
- You can login to the browser using 'username/username' which were generated by using the ansible-playbook `password-generation.yml`


Ensure that `test.domain.com` is added to `/etc/hosts` file

```bash
$ cat /etc/hosts | grep test.domain.com
# 127.0.0.1 test.domain.com
```


#### Directory structure

```bash
$ tree local-mac/task-014-reverse-proxy-nginx-home-using-caddy 
local-mac/task-014-reverse-proxy-nginx-home-using-caddy
├── Caddyfile
├── ReadMe.md
├── certs
│   ├── chained-cert.crt
│   └── private-key.key
├── docker-compose.yml
├── index.html
├── nginx-home
│   └── index.html
└── password-generation.yml
```

- nginx-home/index.html

```bash
hello world from nginx
```

- index.html

```bash
hello world from caddy
```

- Caddyfile

```bash
test.domain.com {
    tls /etc/ssl/certs/chained-cert.crt /etc/ssl/certs/private-key.key

    basicauth * {
            username JDJiJDEyJHNzR25aTkxVajguQk5vVFk3S0h1NXVWNmp5bEtVeHgvOE5VRTJwTGc4dTlkQThTcXV6RlZt
            username2 JDJiJDEyJGhhM21icDczT3BQUXhSRGp6bnpJL2U0c0VTdFc1dDJzTUZjOFNiVDY0RGRKUzBNTDh5aTRl
    }
    reverse_proxy web:80 {
        header_up Host {host}
        header_up X-Real-IP {remote}
        header_up X-Forwarded-For {remote}
        header_up X-Forwarded-Proto {scheme}
    }
}

###
#    root * /usr/share/caddy
#    file_server

### USERS CREATED
# username/username
# username2/username2


###### DEFAULT CADDY FILE - https://caddyserver.com/docs/caddyfile
# :80
# root * /usr/share/caddy
# file_server
# tls /etc/ssl/mycert-chain.crt /etc/ssl/mykey.key
```

- password-generation.yml

```yaml
- hosts: localhost
  gather_facts: false
  tasks:
    - debug:
        msg: "{{ 'username2' | password_hash('bcrypt') | b64encode }}"
```