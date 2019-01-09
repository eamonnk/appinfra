
Representational State Transfer (REST) APIs are service endpoints that support sets of HTTP operations (methods), which provide create, retrieve, update, or delete access to the service's resources.

Azure provides comprehensive set of REST APIs for Azure Services which are available to use. For a the full list of available APIs for each Azure service, see the page <a href="https://docs.microsoft.com/en-us/rest/api/?view=Azure" target="_blank"><span style="color: #0066cc;" color="#0066cc">REST API Browser</span></a>.


Additional API specific services also available on Azure are:

- <a href="https://docs.microsoft.com/en-us/azure/api-management/" target="_blank"><span style="color: #0066cc;" color="#0066cc">API Management service</span></a>, which allows you to publish APIs to external, partner, and employee developers securely and at scale.
- <a href="https://www.microsoft.com/en-us/maps/choose-your-bing-maps-api" target="_blank"><span style="color: #0066cc;" color="#0066cc">BING Maps API service</span></a>, which allows you leverage Bing maps services for locations, routes, fleet tracking and many other mapservices.


### Components of a REST API request/response
A REST API request/response pair can be separated into five components:

1. The request URI, which consists of: 

```http
{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}. 
```

- Although the request URI is included in the request message header, we call it out separately here because most languages or frameworks require you to pass it separately from the request message.

    - URI scheme: Indicates the protocol used to transmit the request. For example, http or https. 
    - URI host: Specifies the domain name or IP address of the server where the REST service endpoint is hosted, such as graph.microsoft.com. 
    - Resource path: Specifies the resource or resource collection, which may include multiple segments used by the service in determining the selection of those resources. 
    - Query string (optional): Provides additional simple parameters, such as the API version or resource selection criteria.


2. HTTP request message header fields:
A required HTTP method (also known as an operation or verb), which tells the service what type of operation you are requesting. Azure REST APIs support **GET**, **HEAD**, **PUT**, **POST**, and **PATCH** methods.


3. Optional additional header fields, as required by the specified URI and HTTP method. For example, an Authorization header that provides a bearer token containing client authorization information for the request.



4. HTTP response message header fields:
An HTTP status code, ranging from 2xx success codes to 4xx or 5xx error codes. 


5. Optional HTTP response message body fields:
MIME-encoded response objects are returned in the HTTP response body, such as a response from a GET method that is returning data. Typically, these objects are returned in a structured format such as JSON or XML, as indicated by the Content-type response header. 

> **Note**: For additional details see the video <a href="https://docs.microsoft.com/en-us/rest/api/azure/" target="_blank"><span style="color: #0066cc;" color="#0066cc">How to call Azure REST APIs with Postman</span></a>.