# Kubernetes - Multiple Containers in a Pod

Let’s create multiple containers in a Pod using a YAML file. We'll use the Busybox container to get the default page served by the Nginx container.

## Create the pod

    kubectl create -f two-containers.yaml

## Get some info

    kubectl get pods -o wide
    kubectl describe pod two-containers

## Connect to the BusyBox container

    kubectl exec -it two-containers --container mybox -- /bin/sh
    # if above fails try below
    kubectl exec -it two-containers -c mybox -- sh

If following fails, can check the docker container id with `docker ps` and then execute following command `docker exec -it <first-3-digits-of-container-id> sh`

## Fetch the HTML page served by the Nginx container

This will output the content of the Web page in the terminal.

    wget -qO- localhost

Reason port was not specified was because NGINX by default listens to PORT 80. If the port we opened was 81 etc we would need to do localhost:{PORT}

## Quit

    exit

## Cleanup

    kubectl delete -f two-containers.yaml --force --grace-period=0
