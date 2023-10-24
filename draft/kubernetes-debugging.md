🔍 Demystifying Kubernetes Debugging: A Simple Guide to the Junior DevOps Enthusiasts

Debugging in Kubernetes can be a multi-faceted process, depending on what you're trying to diagnose. Here's a list of common Kubernetes debugging methods with their respective command examples:

𝐈𝐧𝐬𝐩𝐞𝐜𝐭𝐢𝐧𝐠 𝐏𝐨𝐝 𝐃𝐞𝐭𝐚𝐢𝐥𝐬
Command: kubectl describe pod <POD_NAME> -n <NAMESPACE>
This provides details about the Pod's current state, recent events, and more.

𝐂𝐡𝐞𝐜𝐤𝐢𝐧𝐠 𝐏𝐨𝐝 𝐋𝐨𝐠𝐬
Command: kubectl logs <POD_NAME> -n <NAMESPACE>
This displays the logs of a specific Pod. If the Pod has multiple containers, specify the container with -c <CONTAINER_NAME>.

𝐄𝐱𝐞𝐜𝐮𝐭𝐢𝐧𝐠 𝐂𝐨𝐦𝐦𝐚𝐧𝐝𝐬 𝐈𝐧𝐬𝐢𝐝𝐞 𝐚 𝐂𝐨𝐧𝐭𝐚𝐢𝐧𝐞𝐫
Command: kubectl exec -it <POD_NAME> -n <NAMESPACE> -- /bin/sh
This allows you to run commands inside a container. Replace /bin/sh with the appropriate shell or command.

Inspecting Node Details
Command: kubectl describe node <NODE_NAME>
This provides details about the Node's resources, conditions, and more.

𝐂𝐡𝐞𝐜𝐤𝐢𝐧𝐠 𝐂𝐥𝐮𝐬𝐭𝐞𝐫 𝐄𝐯𝐞𝐧𝐭𝐬
Command: kubectl get events -n <NAMESPACE> --sort-by=.metadata.creationTimestamp
This lists all events in the specified namespace, sorted by their creation timestamps.

Inspecting Network Policies
Command: kubectl describe networkpolicy <POLICY_NAME> -n <NAMESPACE>
This provides details about the network policies applied to the Pods.

Checking ConfigMaps and Secrets
Command for ConfigMaps: kubectl get configmap <CONFIGMAP_NAME> -n <NAMESPACE> -o yaml
Command for Secrets: kubectl get secret <SECRET_NAME> -n <NAMESPACE> -o yaml
These commands display the details of ConfigMaps and Secrets, respectively.

Using Kubectl get with Output Formatting
Command: kubectl get pods -n <NAMESPACE> -o=jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.phase}{"\n"}{end}'
This command lists all Pods in a namespace with their names and statuses using a specific format.

Port Forwarding to Access Services Locally
Command: kubectl port-forward <POD_NAME> <LOCAL_PORT>:<POD_PORT> -n <NAMESPACE>
This allows you to access services running inside a Pod from your local machine.

𝐔𝐬𝐢𝐧𝐠 𝐃𝐞𝐛𝐮𝐠𝐠𝐢𝐧𝐠 𝐓𝐨𝐨𝐥𝐬

Tools like kubectl debug can be used to create debugging sessions. This often requires additional setup.
Command: kubectl alpha debug -it <POD_NAME> -n <NAMESPACE> --image=busybox -- /bin/sh

Inspecting Persistent Volume Claims (PVCs)
Command: kubectl describe pvc <PVC_NAME> -n <NAMESPACE>
This provides details about the PVC's status, events, and more.

Checking Resource Quotas
Command: kubectl describe quota <QUOTA_NAME> -n <NAMESPACE>
This displays the resource quotas set for a namespace & their current usage.


Remember, the exact debugging method and commands to use will depend on the specific issue you're facing. Always refer to the official Kubernetes documentation & consider using monitoring and logging tools for more comprehensive insights.