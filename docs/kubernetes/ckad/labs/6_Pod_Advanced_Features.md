---
title: 6 - Pod Advanced Features
---

1. Create a CronJob that will run the sleep command for 30 seconds. If after 15 seconds it fails, it still runs, make sure it its killed and start the cycle over. 




??? info "Answers"

    `kubectl create cronjob runme --image=busybox --dry-run=client -o yaml --schedule="*/2 * * * *" -- sleep 30 > lab_6.yaml`


    ``` bash
    apiVersion: batch/v1
    kind: CronJob
    metadata:
      creationTimestamp: null
      name: runme
    spec:
      jobTemplate:
        metadata:
          creationTimestamp: null
          name: runme
        spec:
          activeDeadlineSeconds: 15
          template:
            metadata:
              creationTimestamp: null
            spec:
              containers:
              - command:
                - sleep
                - "30"
                image: busybox
                name: runme
                resources: {}
            restartPolicy: OnFailure
      schedule: '* * * * *'
    status: {}           
    ```
