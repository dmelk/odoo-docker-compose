# Odoo community edition docker compose configuration

## Environment variables

### Web server

- `DOMAIN_NAME` - domain name for your odoo instance
- `OWNER_EMAIL` - email for SSL certificate

### Odoo

You need to define next environment variables for odoo instance:

- `DB_PASSWORD` - password for odoo user in postgres database

## Initial setup

Current configuration provides nginx and cerboot to serve odoo instance with SSL. 
For the fist usage you should start nginx server in http only mode and then obtain SLL certificates using cerboot.
To do so you need to start your whole app using next command

```bash
docker compose -f docker-compose.yml -f docker-compose.init.yml up -d
```

Next after everything is up and running, and you got SSL certificate you can simply restart nginx:

```bash
docker compose restart nginx
```