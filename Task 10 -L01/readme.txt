The Nautilus DevOps team needs a time check pod created in a specific Kubernetes namespace for logging purposes. 
Initially, it's for testing, but it may be integrated into an existing cluster later. Here's what's required:

Create a pod called time-check in the xfusion namespace. 
The pod should contain a container named time-check, utilizing the busybox image 
with the latest tag (specify as busybox:latest).

Create a config map named time-config with the data TIME_FREQ=8 in the same namespace.

Configure the time-check container to execute the command: while true; do date; sleep $TIME_FREQ;done. 
Ensure the result is written /opt/itadmin/time/time-check.log. 
Also, add an environmental variable TIME_FREQ in the container, fetching its value from the config map TIME_FREQ key.

Create a volume log-volume and mount it at /opt/itadmin/time within the container.

(I have combined all the manifests in one but they can be separated as well, do run the namespace manifests and then 
configMaps and then pod manfiest respectively)