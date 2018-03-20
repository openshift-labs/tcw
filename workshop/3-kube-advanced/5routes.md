_Services_ provide internal abstraction and load balancing within OpenShift. Sometimes clients (users, systems, devices, etc.) **outside** of the cluster need to access an application. The way that external clients are able to access applications running in OpenShift is through the _Route_ resource. The default OpenShift router (HAProxy) uses the HTTP header of the incoming
request to determine where to proxy the connection. 

By default OpenShift is configured to create the _Route_ based on the _Service_ name being exposed and the _Project_ where the application lives, adding a common subdomain configured at the platform level. In our scenario, we have:

**https://[[HOST_SUBDOMAIN]]-8443-[[KATACODA_HOST]].environments.katacoda.com**.

So let's expose the `stock-con` service (via CLI, so back to the Terminal), using the following command to create a _Route_:

`oc expose service stock-con --port=9898`

Yay! We can get to it now via following URL:

```
http http://stock-con-dok-test.b9ad.pro-us-east-1.openshiftapps.com/average/NYSE:RHT
```


Now that we know how to create a _Route_, let's verify that the  application is really available at the URL shown in the
web console. Click the link and you will see:
