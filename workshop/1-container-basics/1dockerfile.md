A Dockerfile describes how the container is supposed to be constructed. It's a bit like setting up software on a machine: you specify the steps to copy stuff around, install a package or maybe even build stuff from source. Let's have a look at a simple example, a [Node.js app](https://github.com/kubernauts/dok-example-us/blob/master/stock-con/):

<pre class="file" data-filename="Dockerfile" data-target="replace">
FROM mhart/alpine-node:8
MAINTAINER Michael Hausenblas <mhausenb@redhat.com>
WORKDIR /app
COPY dok-example-us/stock-con/ .
RUN npm install express && \
    npm install
USER nobody:nobody
CMD ["node", "service.js"]
</pre>

Now, paste above content—see the copy icon in the lower-right corner of above block—and it will be automatically saved in a file called (surprise!) `Dockerfile` in the current directory.