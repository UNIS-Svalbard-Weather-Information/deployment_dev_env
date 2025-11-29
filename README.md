# Svalbard Weather Information - Developpment Deployment

This repository provide a Docker Compose to setup a developpment environnment with all the services of Svalbard Weather Information.

It is important to note that the configuration is absolutly NOT deployment ready ! DO NOT USE IT for a deployment environnment.

To serve the front end you must first build it directly from the swi-frontend repository and uncomment the corresponding part in nginx.conf and docker-compose.yml .

Services marked as CRON correspond to container that would be run according a CRON schedule (everyday at 15:10 UTC for the seaice for example)

This use NGINX as reverse proxy for the differents services :

- `mapserver.localhost/demo` correspond to the MapProxy server serving the in house layer and caching differents layers from external providers
- `api.localhost/oeapi/v1` provide the Open Elevation API for Svalbard based on NP DEM. See documentation at [Jorl17/open-elevation documentation](https://github.com/Jorl17/open-elevation/blob/master/docs/api.md).
- `api.localhost/public/docs/` provide the swagger interface for the met observation and forecast
