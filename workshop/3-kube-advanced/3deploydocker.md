A simple way to deploy an application in OpenShift is to take an existing container image and run it. We start this exercise in the OpenShift web console so make sure you have it open and that you are in the project called ``dok-stock``.

The Web console provides various options to deploy an application to a project. For now we're going to use the *Deploy Image* method: start with selecting the *Add to Project* button.

Selecting the *Add to Project* button you should be presented with the options of *Browse Catalog*, *Deploy Image* and *Import YAML/JSON*: choose the *Deploy Image* tab now.

On the dialog (with the wonderful fitting name "Deploy Image"), do the following:

- Select the "Image Name" option (radio button)
- Enter the following in the text input field below: `quay.io/mhausenblas/stock-gen:0.3`{{copy}} 
- Hit the magnifying glass icon to the right
- Now OpenShift pulls the metadata from the container registry
- Scroll down a bit until you see the section "Environment Variables" and add the following two:
  - `DOK_STOCKGEN_PORT`{{copy}} with a value of `9999`, and
  - `DOK_STOCKGEN_CRASHEPOCH`{{copy}} with a value of `100`
- Now hit the "Deploy" button and wait a bit

After a minute or so you should see the circle turning blue with "1 pod" in the centre and that means this microservice is deployed, yay.

Now all we need to do is to expose this as service and this we do in the Terminal, so switch to this tab and enter:

`oc project dok-stock`{{execute}}
 
to select your active project and then:

`oc expose dc/stock-gen --port=9999`{{execute}}

to create a service for it.

