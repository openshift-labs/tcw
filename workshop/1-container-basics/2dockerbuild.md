Now we'll build the container image. Note that you really should assign a sensible tag here, never use `latest` (same if you don't specify a tag):

`docker build -t $YOUR_IMAGE_NAME .`{{copy}}

Above, replace the `$YOUR_IMAGE_NAME` with the name of your image. For example, Michael's would look as follows:

`docker build -t quay.io/mhausenblas/stock-con:tcw0 .`

Did it work? Well, let's check:

`docker images`{{execute}}

Do you see your image here? If not, just start over by reloading of this page.

Also, before you proceed make sure that you see an image called `quay.io/mhausenblas/stock-gen:0.3` in the images, there. This one is pulled in the background and you can only do the next step if this one is present.