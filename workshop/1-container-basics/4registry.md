Finally, if you have access to a container registry—we suggest you sign up at [quay.io](https://quay.io/) but Dockerhub will also do—then you can also push the container image you built locally to that registry. If it's a public container image repo, all of your friends and colleagues can readily use it after you've pushed it.

`docker push $YOUR_IMAGE_NAME`{{copy}}

So the full image name `$YOUR_IMAGE_NAME` would be something along the line of:

`$CONTAINER_REGISTRY/$USER/$IMAGE:$TAG`

Note that above structure doesn't have to look like this, different registries expose different conventions but Michael's using quay.io and this one follows the above structure (As do many others).

As a bonus challenge: when you're done with pushing your image, share the URL with your neighbor who could then do a `docker pull …` and run your image ;)
