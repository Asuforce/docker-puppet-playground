# docker-puppet-playground

This is puppet 5 on docker playground

Ubuntu 16:04 with puppet-agent 5.0.0

## first

```
$ git clone git@github.com:Asuforce/docker-puppet-playground.git
$ cd /path/to/docker-puppet-playground
```

## Use Standalone mode

```shell
$ docker build -t puppet:standalone -f Dockerfile-standalone .
$ docker run -itd --name standalone puppet:standalone
$ docker exec standalone puppet apply /etc/puppet/manifests/hello.pp
```

You can see `hello, puppet!`

## Use Standalone mode with librarian-puppet

```shell
$ docker-compose -f module.yml up -d --build
$ docker exec -it module puppet apply /etc/puppet/manifests/nginx.pp --modulepath vendor/modules
```

Access `http://localhost:8080/`

You can see `Hello from Docker Container`


## Use Puppetserver

```shell
$ docker-compose up -d --build
$ docker exec --privileged pmaster systemctl start puppetserver
$ docker exec web001 puppet agent --test --server pmaster.local --environment development
```

Access `http://localhost:8080/`

You can see `Hello from Docker Container`

