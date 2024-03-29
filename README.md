# Medewerkers Register
[![Automated Testing](https://github.com/Huwelijksplanner/MedewerkersRegister/actions/workflows/tests.yml/badge.svg)](https://github.com/Huwelijksplanner/MedewerkersRegister/actions/workflows/tests.yml)

A example implementation of a Common Gateway configuration for generating an API. This example has been specifically setup to use as a temple, read more about that under [Using this repositry as a temple](#Using this repositry as a temple).

- [API Defintion (redocly)](https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/CommonGateway/PetStore/main/OAS.yaml&nocors)
- [API Defintion (file)](https://github.com/CommonGateway/PetStore/blob/main/OAS.yaml)
- [Publiccode](https://github.com/CommonGateway/PetStore/blob/main/publiccode.yaml)
- [Stoplight.io](https://conduction.stoplight.io/docs/huwelijksplanner/qeak2u8mdgl4o-medewerkersregister)

## About Medewerkers Register

## Running the API locally

You need [Docker desktop](https://www.docker.com/) if you want to use this API locally on the [gateway](https://github.com/ConductionNL/commonground-gateway).
Once you have installed docker you need to go to the root of the project with a command line.

Then you can run the image with:

`docker compose up`

If the php container shows "Ready to handle connections" the gateway is ready.
The API runs on port :80 and the endpoints of this API fall under /api

## Running the API online

To run the API on a online gateway the helm secret PUBLICCODE must be set with the url to the raw publiccode.yaml, like: https://raw.githubusercontent.com/Huwelijksplanner/MedewerkersRegister/main/publiccode.yaml

If its properly set you can run the following command in a PHP pod:

`bin/console app:load-publiccodes`

The console should show if the API has been loaded successfully, and then you can make API requests to yourdomain/api.


## (Unit) Testing the API

On every commit github launches a action that generates a postman collection and tests the API. Its results can be viewed under Actions on the github page.

Make sure that in your OAS definition there is a localhost server defined like:
    
    servers:
     - url: localhost/api
