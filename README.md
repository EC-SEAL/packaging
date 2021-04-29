# packaging
Deployment packaging of project services

### Usage guide:

There are two possible configuration options for the packaging deployment:
- docker-compose-ha.yml (HAproxy integration)
- docker-compose-sa.yml (Standalone without HAproxy integration)

#### HAproxy deployment specifications:

In case you choose to deploy the service under an HAproxy load balancer, you have to use the docker-compose-ha.yml file, which is previously filled with the environmental variables required defined, but to fill them with the proper configuration. This is utterly commented across the yaml file.

The second thing to pay attention to when deploying is the mandatory certificate file for the HAproxy. This file is located into the *packaging/haproxy* directory in this very repository, as a form of _*.pem_ file. In it you would find a template for its completion, which consists of a certificate and its private key.

#### Standalone deployment specifications:

For this standalone approach, you will also need to provide the uWSGI instance of the Dashboard service with a valid certificate, but in this case, it will be in a form of a _*.crt_ and _*.key_ pair files, this is just because of the digesting necessities of the uWSGI, and is easily configurable through the environment variables of the docker-compose-sa.yml, the one you shall select in case this standalone deployment is your preference.

To correctly configure these variables you will need to provide the *CERTIFICATE_KEY* name, and also de *CERTIFICATE* name, in the *KEY_PATH* and *CERT_PATH* variables. Keep in mind that the directory where these two files must be located is *certs/*, so you shall not change the first part of this two variables content, as it is presented:

    ```yml
    # Certificate key path mounted in certs directory
    - KEY_PATH=certs/<CERTIFICATE_KEY>.key
    # Certificate path mounted in certs directory
    - CERT_PATH=certs/<CERTIFICATE>.crt
    ```
It is also very important to be aware of the volume declared at the end of the yaml file. It represents the connection between your local certificate/key directory, and the one used within the Docker container. You have to change the very first part of if, represented with the *PATH_TO_CERTIFICATE_AND_KEY_DIRECTORY* string, with your machine directory. It does not need to be named in any particular way, however, it must contain both the *CERTIFICATE_KEY.key*, and the *CERTIFICATE.crt* in it.