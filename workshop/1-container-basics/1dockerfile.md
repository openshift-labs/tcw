A Dockerfile describes how the container is supposed to be constructed. It's a bit like setting up software on a machine: you specify the steps to copy stuff around, install a package or maybe even build stuff from source. Let's have a look at a simple example, a [Dockerfile for a Node.js app](https://github.com/kubernauts/dok-example-us/blob/master/stock-con/Dockerfile):

`
FROM mhart/alpine-node:8
MAINTAINER Michael Hausenblas <mhausenb@redhat.com>
WORKDIR /app
COPY . .
RUN npm install express && \
    npm install
USER nobody:nobody
CMD ["node", "service.js"]
`{{copy}}

Now, paste above content, it will be saved in a file called (surprise!) `Dockerfile` in the current directory.