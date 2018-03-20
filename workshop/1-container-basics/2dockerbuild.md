Now we'll build the container image. Note that you really should assign a sensible tag here, never use `latest` (same if you don't specify a tag):

`docker build -t $YOUR_IMAGE_NAME .`{{copy}}

Above, replace the `$YOUR_IMAGE_NAME` with the name of your image. For example, Michael's would look as follows:

`docker build -t quay.io/mhausenblas/stock-con:tcw0 .`
