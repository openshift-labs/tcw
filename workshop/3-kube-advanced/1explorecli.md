The CLI exposes the underlying Kubernetes orchestration system with the enhancements made by OpenShift. Users familiar with Kubernetes will be able to adapt to OpenShift quickly.

Let's get started by logging into OpenShift. Do the following:

`oc login [[HOST_SUBDOMAIN]]-8443-[[KATACODA_HOST]].environments.katacoda.com --insecure-skip-tls-verify=true`{{execute}}

When prompted, enter the following username and password:

**Username:** ``developer``{{execute}}

**Password:** ``developer``{{execute}}

Next, you can check if it was successful:

`oc whoami`{{execute}}

Should return a response of:

``developer``

That's it!

In the next step, we'll get started with creating your first project using the Web console.
