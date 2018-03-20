A Kubernetes YAML file or manifest defines the container orchestration bits of your application, including but not limited to:

- workloads like [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) or [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- networking related stuff such as [services](https://kubernetes.io/docs/concepts/services-networking/service/) or [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- data and storage related things, for example [volumes](https://kubernetes.io/docs/concepts/storage/volumes/) and [persistent volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
- other things that you as an appops usually don't need to care about, for example [nodes](https://kubernetes.io/docs/concepts/architecture/nodes/) and [access control](https://kubernetes.io/docs/admin/authorization/rbac/)

Let's have a look at a concrete example, so things become clearer. Remember the `stock-gen` and `stock-con` microservices from the previous scenario? We define each of these as an app in Kubernetes, consisting of a `deployment` and a `service`, like so ([source](https://github.com/kubernauts/dok-example-us/blob/master/stock-con/app.yaml)):

<pre class="file">
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  labels:
    app: stock-con
  name: stock-con
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: stock-con
    spec:
      containers:
      - name: stock-con
        image: quay.io/mhausenblas/stock-con:0.3
        env:
        - name: DOK_STOCKGEN_HOSTNAME
          value: stock-gen
        - name: DOK_STOCKGEN_PORT
          value: "9999"
        ports:
        - containerPort: 9898
          protocol: TCP
---
apiVersion: v1
kind: Service
metadata:
  labels:
    app: stock-con
  name: stock-con
spec:
  type: ClusterIP
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 9898
  selector:
    app: stock-con
</pre>