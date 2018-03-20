Next you will create a container based on the image you you created in the previous step:

`docker run --rm --name stock-con -p 80:9898 --link stock-gen:stock-gen -e DOK_STOCKGEN_PORT=9876 -e DOK_STOCKGEN_HOSTNAME=stock-gen $YOUR_IMAGE_NAME`{{copy}}

