OK, so we've deployed our app and can use it from within the cluster.
But what about kicking off a new deployment in the general case? Or how about when our app gets really busy, serving 10x the traffic compared to where we started? How about some horizontal scaling then?

Let's first see how we can trigger a new deployment. For certain changes, such as updating `spec.template.spec.containers[].image` we get a new deployment for free, that is, if you'd change the image from `quay.io/mhausenblas/stock-con:0.3` to `quay.io/mhausenblas/stock-con:0.4` and `kubectl apply …` it, a new deployment is triggered. However, not all changes in the resource spec cause a new deployment being rolled out.

Luckily there's a way to tickle the deployment resource spec to trigger a change (and you can use this trick for any resource change trigger)—simply add an annotation, for example:

`kubectl patch deployment stock-con -p "{\"spec\":{\"template\":{\"metadata\":{\"annotations\":{\"date\":\"$(date +'%s')\"}}}}}"`{{execute}} 

With that out of the way, how about some horizontal scaling? Say we want three identical copies of our stock consumer:

`kubectl scale deploy/stock-con --replicas=3`{{execute}}

Do we have three pods now?

`kubectl get pods -l=app=stock-con`{{execute}}

Note that if you want to idle the app manually you can set `--replicas=0`. This might help with your resource consumption and/or that you stay within quota.

If you want to get rid of the app, you can delete deployments and services with `kubectl delete deploy stock-gen` and `kubectl delete svc stock-gen` and the same for the `stock-con` microservice.