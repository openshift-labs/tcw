Time to actually create something here! Ready? Let's do it :)

First we deploy the `stock-con` app:

`kubectl apply -f dok-example-us/stock-con/app.yaml`{{execute}}

Next up is the `stock-gen` app:

`kubectl apply -f dok-example-us/stock-gen/app.yaml`{{execute}}

Is everything up and running? Let's check:

`kubectl get deploy,svc,po`{{execute}}

See both deployments and services? All pods show their `STATUS` as `Running`? Good, now we're done here. That wasn't too hard, was it now? Note that it make take a few moments before Kubernetes has pulled the images so you might need to execute the `kubectl get …` command above again until you see that all is deployed and running.

Let's see if we can call the two services:

`kubectl run -i -t --rm jumpod --restart=Never --image=quay.io/mhausenblas/jump:v0.1 -- sh`{{execute}}

Now you should be in the `jumpod`, that is inside the cluster, and can `curl` the services like so:

`curl stock-gen:9999/stockdata`{{execute}}

… as well as:

`curl stock-con:80/average/NYSE:RHT`{{execute}}

If you see proper JSON output for both, you may move on, young jedi master!

Don't forget to `exit` from the `jumpod` so that you're back on the prompt of the host (you should see a `master $` now).