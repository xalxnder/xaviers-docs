---
title: 5.4 Generating YAML Files
---

!!! note

    Do not write YAML files, GENERATE them!


To generate YAML files, add `--dry-run=client -o yaml > my.yaml` as an arg to `kubectl run` and `kubectl create`. 

- `dry-run=client` - All this is doing is generating code.


??? example "Generating the YAML"

    === "Generating The YAML"

        ``` yaml
        kubectl run myginx --image=nginx --dry-run=client -o yaml > mynginx.yaml
        ```


    === "mynginx.yaml"


        ``` yaml
        apiVersion: v1
        kind: Pod
        metadata:
        creationTimestamp: null
        labels:
            run: myginx
        name: myginx
        spec:
        containers:
        - image: nginx
            name: myginx
            resources: {}
        dnsPolicy: ClusterFirst
        restartPolicy: Always
        status: {}
        
        ```

??? example "Applying The YAML"

    === "Applying"

        `kubectl apply -f mynginx.yaml`
    

    === "Output"

        ```bash
        pod/myginx created
        ```