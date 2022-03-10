nv-demo -  Adapted from NeuVector's testing section in their documentation.

This repo contains yaml files for deploying redis, nodejs and nginx workloads into a namespace called nv-demo.  These pods will be used to test NeuVector's 'Discover' capabilties.

After deplying the workloads, follow the below:

To generate a violation from a nodejs pod, find a pod:

    kubectl get pod -n nv-demo

Then try some violations (replace node-pod-name):

    kubectl exec <node-pod-name> curl www.google.com -n nv-demo

Find the internal IP address of another node pod, for example 172.30.2.21 and connect to it:

    kubectl exec <node-pod-name> curl 172.30.2.21:8888 -n nv-demo

To simulate an attack, log into a container, then try a ping attack:

    kubectl exec -it <node-pod-name> bash -n nv-demo
    ping <172.30.2.21> -s 40000
    