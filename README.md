# docker-puppet

Ubuntu16:04 with puppet-agent 5.0.0

## Use Standalone mode

1. docker build -t puppet:standalone -f Dockerfile-standalone .
2. docker run -itd --name standalone puppet:standalone
3. docker exec standalone puppet apply /var/puppet/manifests/site.pp
4. You can see `hello, puppet!`
