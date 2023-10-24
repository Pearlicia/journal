3 weeks back while I was working on a Kubernetes project, saw a very common bad practice, i.e. image size is 8 GB which could have been just 436 MB (Multi-stage Build)!!!!

After working on such numerous projects, here I have made a list of best practices for containers:

Use Minimal Base Images:
Start with minimal base images like Alpine Linux or Distroless to reduce the attack surface and improve container startup times.

Single Concern per Container:
Each container should have only one responsibility. If an application has multiple components (e.g., web server, database etc), they should be split into separate containers and managed as separate services.

Stateless Applications:
Design your applications to be stateless as much as possible. This allows Kubernetes to easily scale, restart, or replace containers without losing data.

Liveness and Readiness Probes:
Use liveness probes to let Kubernetes know when to restart a container and readiness probes to know when a container is ready to start accepting traffic.

Resource Limits:
Set resource requests and limits for CPU and memory to ensure that the container gets its required resources and doesn't consume more than it should.

Security:
Run containers with a non-root user.
Use network policies to control communication between pods.
Regularly scan container images for vulnerabilities.
Use Kubernetes RBAC (Role-Based Access Control) to limit permissions.

Immutable Containers:
Avoid making changes to running containers. Instead, create a new container image and deploy it. This ensures consistency across environments.

Use Labels and Annotations:
Use labels for organizing and selecting groups of resources. Annotations can be used to store additional metadata.

Configurations and Secrets:
Use ConfigMaps for non-sensitive configuration data and Secrets for sensitive data. Avoid hardcoding configurations in the container image.

Logging and Monitoring:
Ensure that your applications log to the standard output and standard error streams. This allows Kubernetes to handle and redirect the logs appropriately.
Integrate with monitoring tools like Prometheus to keep an eye on the health and performance of your containers.

Regularly Update and Patch:
Regularly update your container images to include security patches and updates. Use image scanning tools to identify and fix vulnerabilities.

Graceful Shutdown:
Ensure that your applications handle the SIGTERM signal and shut down gracefully. This allows them to finish processing current requests and release resources before shutting down.

Avoid Using latest Tag:
Be explicit with container image tags. Avoid using the latest tag as it can lead to unpredictable deployments.

Storage Considerations:
If your application needs persistent storage, use Persistent Volumes (PV) and Persistent Volume Claims (PVC) in Kubernetes. Ensure that the storage solution you choose is compatible with the dynamic nature of containerized deployments.