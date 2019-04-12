# Platform

Assuming there is already a given configuration for Servers, Networking and Operating systems, lets see the platform layer in the web apps.

In the front-end the platform is usually the browser with the Rendering engine the JavaScript engine and all the features provided by the web browser.

In the back-end the platform is a web server plus the operating system, the database, and any other software service (daemon) in charge of providing resources to our application, so it could be very heterogenous.

## Web Servers

![](https://icon2.kisspng.com/20180325/jsw/kisspng-web-server-computer-servers-web-hosting-service-da-server-5ab7407da4d035.1136060515219590376751.jpg)

```
Client -> Server
            |
            HTML pages
            Assets
```

* Support the HTTP protocol and optionally HTTPS.
* Some form of cache for static assets (images,css,scripts)
* Optionally could provide header rewritting and multiple sites support. (e.g. web.site.com.py / mail.site.com.py)

![](http://www.uptimemadeeasy.com/wp-content/uploads/2013/12/Apache_Reverse_Proxy.jpg)

Some examples are:

* Apache Httpd : Popular full featured web server, de facto standard in a lot of Operating Systems.

* IIS : Microsoft Web server, with additional support for Microsoft Technologies like (ASP)

* NginX : Lightweight web server used mostly as load balancer, proxy, reverse proxy or any other pattern where acts as intermediate.

### Reverse Proxy

Remember the traditional proxy architecture

#### Proxy

```
Client -> Proxy -> Wild Internet -> Server
```

From this the reverse one is 

#### Reverse Proxy 

Only handle message forwarding between the client and the desired server, usually based on the Host header

```
                            200.10.229.169
                            (pol.una.py)
Client -> Wild Internet -> Reverse Proxy ---> Server 1 (www.pol.una.py)
                                         \--> Server 2 (mail.pol.una.py)
                                          \-> Server 3 (ftp.pol.una.py)
                                           \> Server 4 (static.pol.una.py)
All the internal IPs are private
```

A traditional example in NginX

![](https://ericlondon.com/images/nginx_diagram.png)

### Gateway Server / API Gateway

The same as Reverse proxy BUT, the gateway could handle some logic, like:

* authentication
* throttling
* dynamic configuration
* service discovery
* service registry

![](https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Fcdn.wp.nginx.com%2Fwp-content%2Fuploads%2F2016%2F04%2FRichardson-microservices-part2-3_api-gateway.png&f=1)

### Modules

Modules are extensions to Web servers, giving them support for other protocolos and other languages 

* mod_php (The server understand PHP)
* mod_python (The server understand Python)
* wsgi (The server could communicate with other application servers and work as proxy)
* AJP (The server support a communication protocol with JAVA Application Servers).

## Application Server

* Apache Tomcat

![](https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.CNKAWV1xj0ny4VbUwZa_mgHaHa%26pid%3DApi&f=1)
![](https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.ha97.com%2Fwp-content%2Fuploads%2F2012%2F05%2Ftomcat-manager.jpg&f=1)

* Jboss/Wildfly

![](https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.3pillarglobal.com%2Fwp-content%2Fuploads%2F2016%2F03%2Fwildflyfeatured-300x300.png&f=1)
![](https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fblog.arungupta.me%2Fwp-content%2Fuploads%2F2015%2F08%2Fwildfly10-beta2-configuration.png&f=1)
![](https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.slidesharecdn.com%2Fmarchioni-wildfly-2014-140417053428-phpapp02%2F95%2Fintroduction-to-wildfly-8-marchioni-7-638.jpg%3Fcb%3D1398763917&f=1)

* Glasfish

* Phussion Passenger

* Gunicorn


## Load balancer

A single point of access doing forwarding connection to different servers based on load meassure. the servers behind are exact clones, serving the same application.

```
                        web.pol.una.py
Client -> Wild Internet -> Load Balancer ---> Server 1 (wa1.pol.una.py)
                                         \--> Server 2 (wa2.pol.una.py)
                                          \-> Server 3 (wa3.pol.una.py)
                                           \> Server 4 (wa4.pol.una.py)
```

This approach is a de facto standard in scalability, but have some considerations to make.

## Mixing

In real life Scenarios the pure web servers are used also with application servers in order to separate request handling from bussiness logic processing, this was an usual scenario

![](http://4.bp.blogspot.com/-8nlx0XhN_4I/TbdvSdtlAAI/AAAAAAAAKzw/zCNZG-lprDw/s1600/securing-tomcat-with-apache-web-server.png)