The Metrics Server is an essential component for gathering resource utilization metrics (such as CPU and memory) from your Kubernetes cluster, and it is required for Horizontal Pod Autoscaling (HPA) to work correctly. Here are the steps to deploy the Metrics Server in your Kubernetes cluster:

wget https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

kubectl apply -f components.yaml

kubectl get deployment metrics-server -n kube-system

The output should show the AVAILABLE replicas as 1, indicating that the Metrics Server is running.

Wait for Metrics Collection:
It may take a few minutes for the Metrics Server to start collecting data from your cluster nodes. After deployment, give it some time to collect metrics.

Test Metrics Server:
You can test whether the Metrics Server is functioning correctly by querying for some metrics. For example, you can check the CPU usage of pods:

kubectl top pods

This command should return information about CPU usage for your running pods.

Once the Metrics Server is deployed and collecting metrics, you can set up HPAs