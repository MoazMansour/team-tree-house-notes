# HTTP Basics

HTTP stands for HyperText Transfer Protocol and represents a format of communication between two devices over the internet.

### Notes

-   HTTP is a plain text protocol. Which means messages sent through HTTP are driectly readable.
-   HTTP itself is what is called the "Stateless" protocol.

**Stateless**

> `Stateless`: means there's no record of previous interactions, and each interaction is processed only with the information that comes with that particular interaction.

**Telnet**

> `Telnet`: It is a little piece of software that's designed for connecting to and communicating with a remote device.

**httpbin**

> `httpbin.org` is a service specifically designed for testing HTTP requests and seeing resulting responses.

**What is Port Numbers?**

> -   Think about the host or domain name as a physical address, which is known on the web as IP address.
> -   Ports are doors to different units in the address, each speak a different language. Port 80 is for the HTTP language.
> -   At the same address/port number, there might be several host. You might need to list the hostname again in the HTTP request so that you get directed to the right host.

**Slashes**

> Slashes are usually used to refer to a directory in the server, but this doesn't have to be the case all the time. It can be used to annotate resources addresses on a host like in `/xml`

**Definitions:**

> -   **URI:** Uniform Resource Identifier.
> -   **URL:** Uniform Resource Locator. URL is a URI tha also contains information on how to locate the resource.
> -   **XML:** Extensible Markup Language.

### HTTP Request Format

**Request Formt**

> **Request-Line:** `GET|Post [uri] HTTP/[version]`
>
> **Headers:** `[HEADER Name]: [Header Value]` (each on its own line)
>
> **Blank Line:**  ``
>
> **Request Body:** aka payload (Optional, only for POST requests)

**Types**

> **Requests Types:** There are several HTTP request types we are covering just two of them here.
>
> -   `GET`: Generally is a request to view a resource on the server.
> -   `POST`: Used for making a change to a resource or creating one.

### HTTP Response Format

**Response Format**

> **Status-Line:** `HTTP/[version] [status code] [status message]`
>
> **Headers:** `[HEADER Name]: [Header Value]` (each on its own line)
>
> **Blank Line:**  ``
>
> **Payload:** requested resource.

**Types**

> **Response Status Types:** There are several of this two as an exmaple
>
> -   `200`: A 200 response code generally means Okay.
> -   `400`: A message in the 400s like a `404: Not Found` usually means something that went wrong on the client's request.
> -   `300`: Indicates that the resource requested may have moved. The rest of the response contains instructions about where to find it.
> -   `500`: Used for indicating that something went wrong on the server side.

**Content-Length**

>   Whenever a response returns that contains a payload, the `Content-Length` header will be present. The value it carries indicates the length or the size of the response in bytes.

### Forms

**Components**

-   Form tags
-   Form method attribute - optional, defaults to "get"
-   Form action attribute
-   Form elements for users to provide info
-   Submit button - optional, triggered with ENTER

**Form Tags**

> Contains two attributes: method and action.
> Method attribute can be either `get` or `post`, when ommitted is assumed to be `get`
>
> The "action" attribute referes to the absolute or relative URL to which the form will be submitted.

**Form elements**

> -   input of type text for any string input like username and password
> -   radio buttons.
> -   checkboxes.
> -   select elements for dropdowns
> -   Text area elements for long text
> -   hidden inputs with predetermined values
