---
title: 5 - Pod Basic Features
---
1. Create a YAML file that meets the following requirements:
    - A Namespace with the name "microservice" is created.
    - A Pod with the name "microdb", based on the mariadb image is started in this Namespace.
2. Create the resources using the declarative methodology.



??? info "Answers"

    `kubectl create ns microservice --dry-run=client -o yaml > lab.yaml`

    `kubectl run microdb --image=mariadb --env MARIADB_ROOT_PASSWORD=password -n microservice --dry-run=client -o yaml >> labs.yaml`

    ``` bash
    #lab.yaml
    ---
    apiVersion: v1
    kind: Namespace
    metadata:
    creationTimestamp: null
    name: micro
    spec: {}
    status: {}

    ---
    apiVersion: v1
    kind: Pod
    metadata:
    creationTimestamp: null
    labels:
        run: microdb
    name: microdb
    namespace: micro
    spec:
    containers:
    - env:
        - name: MARIADB_ROOT_PASSWORD
        value: password
        image: mariadb
        name: microdb
        resources: {}
    dnsPolicy: ClusterFirst
    restartPolicy: Always
    status: {}
    ```