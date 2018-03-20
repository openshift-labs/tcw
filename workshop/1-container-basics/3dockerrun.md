Next you will create a container based on the image you created in the previous step:

`docker run --rm --name stock-con -p 8080:9898 --link stock-gen:stock-gen -e DOK_STOCKGEN_PORT=9876 -e DOK_STOCKGEN_HOSTNAME=stock-gen $YOUR_IMAGE_NAME`{{copy}}

Again, make sure that you replace the `$YOUR_IMAGE_NAME` with whatever you selected for your image name (incl. a tag).

Now, you can check if it worked correctly by issuing the following command in a new terminal session (click the `+` button):

`curl localhost:8080/average/NYSE:RHT`{{execute T2}}

Or, you can click on the `Web Preview` pane and whatever URL comes up there, you append `average/NYSE:RHT`.
