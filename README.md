# Ansible-ELK

Installs ELK and other cools ELK related things.

# Requirements

To Do


## Getting started

To Do

### Generating a Self-signed certificate

For utmost security, you should use your own valid certificate and keyfile, and update the logstash_ssl_* variables in your playbook to use your certificate.
To generate a self-signed certificate/key pair, you can use use the command:

```openssl req -x509 -batch -nodes -days 3650 -newkey rsa:2048 -keyout logstash.key -out logstash.crt -subj '/CN=example.com'```

Note that Filebeat and Logstash may not work correctly with self-signed certificates unless you also have the full chain of trust (including the Certificate Authority for your self-signed cert) added on your server. See: https://github.com/elastic/logstash/issues/4926#issuecomment-203936891

Newer versions of Filebeat and Logstash also require a pkcs8-formatted private key, which can be generated by converting the key generated earlier, e.g.:

```openssl pkcs8 -in logstash.key -topk8 -nocrypt -out logstash.p8```

### Another way of generating the certificates

Follow this link for another guide on how to create the certificates:

https://www.elastic.co/blog/configuring-ssl-tls-and-https-to-secure-elasticsearch-kibana-beats-and-logstash#create-ssl

Once you have generated the certificates, you will need to fill out the playbooks accordingly.
