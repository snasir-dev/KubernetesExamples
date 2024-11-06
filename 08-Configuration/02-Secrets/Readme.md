# L28-04

To quickly encode/decode strings into base64

    https://www.base64encode.org/
    https://www.base64decode.org/

or on Windows, install base64

    choco install base64

on Linux/Mac

    echo [string] | base64
    echo [encodedString] | base64 -d

## Create the Secrets

    kubectl apply -f secrets.yaml -f pod.yaml

## Look at the secrets

    kubectl get secret
    # Only shows the # of bytes. No characters
    kubectl describe secret secrets

    # MUCH MORE HELPFUL COMMAND
    kubectl get secret app-secrets -o YAML

## Connect to the Busybox

    kubectl exec mybox -it -- sh

## Display the USERNAME and PASSWORD env variables

    # list all env variables on machine. It does not encode them here
    # It will say the decoded values of USERNAME/PASSWORD when you run cmd "env"
    env
    echo $USERNAME_TEST
    echo $PASSWORD
    exit

## Cleanup

    kubectl delete -f secrets.yaml -f pod.yaml --force --grace-period=0

## Secrets Cheatsheet

![alt text](image.png)
