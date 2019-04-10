# OpenLdap
Install and configure OpenLdap using Docker and Docker-compose

LDAP stands for Lightweight Directory Access Protocol. As the name suggests, it is a lightweight protocol for accessing directory services, specifically X.500-based directory services. LDAP runs over TCP/IP or other connection oriented transfer services.

What kind of information can be stored in the directory? The LDAP information model is based on entries. An entry is a collection of attributes that has a globally-unique Distinguished Name (DN). The DN is used to refer to the entry unambiguously. Each of the entry's attributes has a type and one or more values. The types are typically mnemonic strings, like "cn" for common name, or "mail" for email address. The syntax of values depend on the attribute type. For example, a cn attribute might contain the value Babs Jensen. A mail attribute might contain the value "babs@example.com". A jpegPhoto attribute would contain a photograph in the JPEG (binary) format.


You can install on Physical Machine/Virtual machine using apt/yum package installer according to your Linux Distribution but if you want to use in docker container. You can use docker command or docker-compose method of deployment.

# Run docker container with docker command.

<pre>docker run -d --name openldapcontainer  -e SLAPD_PASSWORD=password -e SLAPD_DOMAIN=gotechnies dinkel/openldap </pre>

#To start and link the PhpLdapAdmin follow the below command

<pre> docker run -d -p 80:80 --link openldapcontainer:openldap dinkel/phpldapadmin </pre>

The simple and easy deployment is also available.

clone this repository
<pre>
git clone https://github.com/arvindr226/OpenLdap
cd OpenLdap
docker-compose -d up
</pre>

If docker-compose doesn't exist on your system, to install docker-compose on Linux machine
<pre>
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
</pre>

After docker comes up using the http://ipofyourmachin or http://localhost you will be getting phpLdapAdmin dashboard.
Use the below credentials to get logIn
<pre>
username=cn=admin,dc=gotechnies,dc=com
password=password
</pre>


Reference Links-:
https://www.openldap.org/
https://github.com/dinkel/
https://docs.docker.com/compose/install/
