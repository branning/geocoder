## Geocoder Proxy

A RESTful web service in Python that gives latitude and longitude coordinates for addresses. The service itself does not have any geolocation smarts, but instead it serves as an interface to other services that do.

### Reverse Geocoding Backends

These services are supported:

- [Google Maps Places API](https://developers.google.com/maps/documentation/geocoding/start)
- [HERE Geocoder API](https://developer.here.com/documentation/geocoder/topics/quick-start.html)

### Configuration

This project follows the configuration practices of [12 Factor Apps](https://12factor.net/), and stores its configuration in the environment. For instance, the API keys for the geocoder backends are provided to the application this way.

The [envparse](https://github.com/rconradharris/envparse) package is used to aid this process, and allows loading envronment variables from a convenient `.env` file.

### API Server

The RESTful endpoints are defined in [OpenAPI / Swagger 2.0](https://swagger.io/solutions/getting-started-with-oas/) format, and can be found in [swagger/geocoder.yaml](./swagger/geocoder.yaml). Clients for the API can be generated using that file, and API documentation is also generated from it.

### Testing

Unit tests are written using [pytest](https://docs.pytest.org/en/latest/).

Integration tests of the running API server use the [HTTPie](https://httpie.org/) client. You could also use the example cURL commands from the Swagger documentation.

### Security

The server will refuse to run without HTTPS. Self-signed certificates are generated automatically using [openssl](https://letsencrypt.org/docs/certificates-for-localhost/)

