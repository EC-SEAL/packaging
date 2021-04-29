# packaging
Deployment packaging of project services

### Usage guide:

There are two possible configuration options for the packaging deployment:
- docker-compose-ha.yml (HAproxy integration)
- docker-compose-sa.yml (Standalone without HAproxy integration)

#### HAproxy deployment specifications:

This configuration deployment option is for the HAproxy integration, you have to add the cerficate for the SSL in the /haproxy folder for 

#### Standalone deployment specifications:

* For the standalone integration with no HAproxy, it is needed the definition of a volume for the certificate directory. The entry for this configuration is declared as <PATH_TO_CERTIFICATE_AND_KEY_DIRECTORY>. 
