Next you will create a container based on the image you you created in the previous step:

`docker run --rm -p 9898:9898 \
            -e DOK_STOCKGEN_PORT=9876 \
            -e DOK_STOCKGEN_HOSTNAME=localhost \
            $YOUR_IMAGE_NAME`{{copy}}

