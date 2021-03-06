# openstack-proxy

Simple proxy server for OpenStack Swift storage

# Usage

First, edit .env and put valid values in there for swift authentication, secret keys etc.

If you want to use SSL and HTTPS put the following files in the root directory of the app:
- ssl_file.key
- ssl_file.crt

or just generate those files running (for testing https in development mode):
```
./bin/generate_ssl_certificates
```

Next run the app. There are two modes available, ie.

Standalone:
```bash
$ npm install
$ NODE_ENV=<production|development> npm start
```

In a Docker container:
```bash
$ ./bin/dockerize
$ docker exec -ti os-proxy pm2 reload --env <production|development> os-proxy.yml'
```

You can now connect to docker shell by running:
```bash
$ ./bin/shell_to_docker
```

Inside docker (or when running without docker):

1. ```$ pm2 status``` - shows status of running applications
2. ```$ pm2 reload <app-name|all>``` - reloads selected app or all apps
3. ```$ pm2 stop <app-name|all>``` - stops selected app or all apps
4. ```$ npm test``` - runs test script dfined in package.json

# TODO
- Add some file validation?
- How to run it with different environments (ie. dev, prod, staging etc.)?
