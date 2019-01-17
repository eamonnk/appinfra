
*Representational State Transfer* (REST) APIs are service endpoints that support sets of HTTP operations (methods).  APIs support HTTP methods by facilitating create, retrieve, update, or delete access to the service's resources.

Azure provides a comprehensive set of REST APIs for Azure Services which are available to use. For a the full list of available APIs for each Azure service see the page [REST API Browser](https://docs.microsoft.com/en-us/rest/api/?view=Azure).

Additional API specific services available on Azure include:

- [API Management service](https://docs.microsoft.com/en-us/azure/api-management/) allows you to publish APIs to external, partner, and employee developers securely and at scale.
- [BING Maps API service](https://www.microsoft.com/en-us/maps/choose-your-bing-maps-api) allows you leverage Bing maps services for locations, routes, fleet tracking and many other map services.

### Components of a REST API request/response

A REST API request/ response pair can be separated into five components.

:one: *The request URI*. The request URI consists of:

  ```http
    {URI-scheme} :// {URI-host} / {resource-path} ? {query-string}.
  ```

  - *URI scheme*. Indicates the protocol used to transmit the request. For example, http or https.
  - *URI host*. Specifies the domain name or IP address of the server where the REST service endpoint is hosted, such as graph.microsoft.com.
  - *Resource path*. Specifies the resource or resource collection, which may include multiple segments used by the service in determining the selection of those resources.
  - *Query string (optional)*. Provides additional simple parameters, such as the API version or resource selection criteria.

  > :information_source:  Although the request URI is included in the request message header, we call it out separately here because most languages or frameworks require you to pass it separately from the request message.

:two: *HTTP request message header fields*. This is a required HTTP method (also known as an operation or verb), which tells the service what type of operation you are requesting. Azure REST APIs support `GET`, `HEAD`, `PUT`, `POST`, and `PATCH` methods.

:three: *Optional additional header fields*. Additional header fields are required by specific URI and HTTP methods. For example, an Authorization header that provides a bearer token containing client authorization information for the request.

:four: *HTTP response message header fields*. These are HTTP status codes, which range from 2xx success codes to 4xx or 5xx error codes.

:five: *Optional HTTP response message body fields*. MIME-encoded response objects are returned in the HTTP response body, such as a response from a GET method that is returning data. Typically, these objects are returned in a structured format such as JSON or XML, as indicated by the Content-type response header.

> :information_source: For additional details see the video [How to call Azure REST APIs with Postman](https://docs.microsoft.com/en-us/rest/api/azure/).
