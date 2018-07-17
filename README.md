# MLR-Validator-Docker
Docker configuration to deploy the MLR-Validator service in a Docker container 

[![Build Status](https://travis-ci.org/USGS-CIDA/MLR-Validator-Docker.svg?branch=master)](https://travis-ci.org/USGS-CIDA/MLR-Validator-Docker)


The two docker files provided pull the artifact from cida.usgs.gov/artifactory. The artfact_version should be the version of the usgs-wma-mlr-validator that you want to be used in the docker container. The ENV 'listening_port' can be specified and defaults to 7010. This port will be exposed by the container. 
To build within the DOI network place the DOI cert in '/DOIRootCA.crt'. Below is an example of how to build.

To run, you can specify a bind mount on the host system where you want the exported files written (the src part of the bind), and create a compose.env file locally and set the ENV variables as desired:
```
oauthResourceTokenKeyUri=https://path.com/to/token_key\
jwt_algorithm=HS256 \
jwt_decode_audience=string_in_aud_claim_in_token \
ssl_cert_path=path_to_auth_cert or False (not recommended) if disabling SSL verification \
authorized_roles='admin, developer' # Comma separate list of roles that will be allowed
```

Below is an example:
```bash
docker run --publish 5000:7010 \
    validator
```