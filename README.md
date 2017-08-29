# docker-puppet-playground

This is puppet 5 on docker playground

Ubuntu 16:04 with puppet-agent 5.0.1

## first

```console
$ git clone git@github.com:Asuforce/docker-puppet-playground.git
$ cd /path/to/docker-puppet-playground
```

## Use Standalone mode

```console
$ docker build -t puppet:standalone -f Dockerfile-standalone .
$ docker run -itd --name standalone puppet:standalone
$ docker exec standalone puppet apply /etc/puppet/manifests/hello.pp
```

You can see `hello, puppet!`

## Use Standalone mode with librarian-puppet

```console
$ docker-compose -f module.yml up -d --build
$ docker-compose exec module puppet apply /etc/puppet/manifests/nginx.pp --modulepath vendor/modules
```

Access `http://localhost:8080/`

You can see `Hello from Docker Container`

## Use Puppetserver

```console
$ docker-compose up -d --build
$ docker-compose exec pmaster systemctl start puppetserver
$ docker-compose exec web001 puppet agent --test --server pmaster --environment development
```

Access `http://localhost:8080/`

You can see `Hello from Docker Container`

