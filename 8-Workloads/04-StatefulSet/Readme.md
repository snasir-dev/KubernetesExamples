# Kubernetes StatefulSet

Let's now create a StafulSet.

## Create the Deployment

    kubectl apply -f statefulset.yaml

## Get the pods list

    kubectl get pods -o wide

## Get a list of the PersistentVolumes Claims

    kubectl get pvc

## Create a file in nginx-sts-2

Open a session in nginx-sts-2 and create a file in the folder mapped to the volume.

    kubectl exec nginx-sts-2 -it -- bash
    cd var/www
    echo Hello World > hello.txt

## Modify the default Web page

    cd /usr/share/nginx/html
    # Replace the default nginx index.html file contents with our contents
    cat > index.html
    Hello World - index.html
    Ctrl-D
    exit

Now the file should just have the following text: `Hello World - index.html`

## Open a session in nginx-sts-0 and reach nginx-sts-2

    kubectl exec nginx-sts-0 -it -- bash
    # Name of Instance (Pod) + Name of Headless Service.
    # http://{STATEFULSET_PODNAME_TO_REACH}.{NAME_OF_SERVICE}
    curl http://nginx-sts-2.nginx-headless
    exit

## Delete pod 2

Delete a pod and watch as it is AUTOMATICALLY RECREATED with the SAME name `nginx-sts-2`.

    kubectl delete pod nginx-sts-2

## Is the file still there?

Open a session in nginx-sts-2 and see if the file is still present.

    kubectl exec nginx-sts-2 -it -- bash
    ls var/www
    exit

## Cleanup

    kubectl delete -f statefulset.yaml
    kubectl delete pvc www-nginx-sts-0
    kubectl delete pvc www-nginx-sts-1
    kubectl delete pvc www-nginx-sts-2
