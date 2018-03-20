Here you'll learn how to use [OpenShift](https://www.openshift.org) to build and deploy apps.

OpenShift incorporates several upstream projects (Kubernetes, Docker/CRI-O, HAProxy, Open vSwitch, etc.) while also providing additional features and functionality to make those upstream projects easier to consume.

No matter if you're a developer or an operator, you've got the following options to communicate with OpenShift:

- Command Line Interface (CLI) … is called the `oc` tool, written in Go, and a super-set of `kubectl`.
- Web Console … OpenShift also provides a feature rich Web console that provides a friendly graphical interface for interacting with the platform.
- HTTP API … both the CLI and the Web console communicate with OpenShift via the same method, the [HTTP API](https://docs.openshift.org/latest/rest_api/index.html).
