# A small guide for troubleshooting Kubernetes issues! 🚀

## Checking Pod Status

```
kubectl get pods -n <namespace>
```

Use this command to list all pods in the specified namespace along with their statuses. Check the `STATUS` column to identify any pods that are not running or have errors.

---

## Checking Pod Logs

```
kubectl logs <pod_name> -n <namespace>
```

Use this command to retrieve the logs of a specific pod in the specified namespace. Replace `<pod_name>` with the name of the pod you want to inspect.

---

## Describing Pods

```
kubectl describe pod <pod_name> -n <namespace>
```

This command provides detailed information about a specific pod, including its status, containers, events, and more. It helps in diagnosing issues related to pod creation, scheduling, and configuration.

---

## Checking Node Status

```
kubectl get nodes
```

Use this command to list all nodes in the cluster along with their statuses. Check the `STATUS` column to ensure all nodes are in the `Ready` state. Nodes in other states may indicate network or hardware issues.

---

## Restarting Pods

```
kubectl delete pod <pod_name> -n <namespace>
```

In some cases, restarting a pod can resolve issues related to application crashes or misconfigurations. Use this command to delete a pod, which will trigger Kubernetes to create a new one.

---

## Checking Events

```
kubectl get events -n <namespace>
```

Events provide insights into the state changes and actions performed by Kubernetes components. Use this command to list all events in the specified namespace and identify any anomalies or error messages.

---

## Scaling Deployments

```
kubectl scale deployment <deployment_name> --replicas=<replica_count> -n <namespace>
```
Use this command to scale the number of replicas in a deployment. Adjust the `<replica_count>` to the desired number of instances.

---

## Checking Resource Usage

```
kubectl top pods -n <namespace>
```

This command provides resource usage metrics for pods in the specified namespace, including CPU and memory utilization. It helps identify pods that are consuming excessive resources.

---

## Deleting Stuck Pods

```
kubectl delete pod <pod_name> --grace-period=0 --force -n <namespace>

```

Use this command to forcefully delete a stuck pod that is not responding to regular deletion attempts.

---

## Inspecting Service Endpoints

```
kubectl get endpoints <service_name> -n <namespace>
```

This command displays the endpoints associated with a Kubernetes service, helping verify connectivity and routing.

---

## Checking Persistent Volume Claims

```
kubectl get pvc -n <namespace>
```

Use this command to list all persistent volume claims (PVCs) in the specified namespace, ensuring they are bound to available volumes.

---

## Debugging Pods Interactively

```
kubectl exec -it <pod_name> -n <namespace> -- /bin/bash
```

This command opens an interactive shell inside the specified pod, allowing you to debug issues by executing commands directly.

---

## Inspecting Network Policies

```
kubectl get networkpolicies -n <namespace>
```

Use this command to list all network policies applied in the specified namespace, ensuring they allow necessary communication between pods.

---

## Analyzing Container Images

```
kubectl describe pod <pod_name> -n <namespace> | grep "Image:"

```

This command extracts and displays the container images used by a specific pod, facilitating analysis of image versions and dependencies.

---

## Debugging Service Connectivity

```
kubectl run --generator=run-pod/v1 --rm -i --tty net-tools --image=alpine:3.13 --restart=Never -- /bin/sh

```
This command creates a temporary pod with network troubleshooting tools (such as `ping`, `nslookup`, etc.) for diagnosing connectivity issues.

---

## Analyzing Kubernetes Events

```
kubectl get events -n <namespace> --sort-by=.metadata.creationTimestamp

```
Use this command to list events in the specified namespace, sorted by creation timestamp, to identify recent changes or errors.

---

## Monitoring Pod CPU Usage

```
kubectl top pod <pod_name> -n <namespace>

```
This command provides real-time CPU usage metrics for a specific pod in the specified namespace.

---

## Checking API Server Logs

```
kubectl logs -n kube-system <api_server_pod_name> kube-apiserver

```
This command retrieves logs from the Kubernetes API server pod, helpful for diagnosing issues related to API requests and responses.

---

## Inspecting Cluster Roles

```
kubectl get clusterroles -n <namespace>

```
This command lists all cluster roles defined in the specified namespace, ensuring proper permissions for accessing resources.

---

## Debugging DNS Resolution

```
kubectl run --generator=run-pod/v1 --rm -it busybox --image=busybox:1.28 --restart=Never -- nslookup <domain_name>

```
This command creates a temporary pod with the `busybox` image and performs DNS resolution for the specified `<domain_name>`, helping diagnose DNS-related issues.