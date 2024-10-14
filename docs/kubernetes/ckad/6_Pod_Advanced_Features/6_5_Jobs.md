---
title: 6.4 Jobs
---

In Kubernetes, a Job is a resource used to run tasks that need to be completed successfully once or a specific number of times. Unlike a Deployment or Pod, which manages long-running services or applications, a Job ensures that a particular task, such as a batch job or short-lived process, is completed successfully. Once this job is complete, though, you should use `spec.ttlSecondsAfterFinished` to clean up completed jobs automatically

## Job Types
- Non Parallel:
    - Only one Pod is started, unless the Pod fails.
    - The Job is complete as soon as its Pod terminates successfully
- Parallel Jobs:
    - Specify a non-zero positive value for .spec.completions.
    - The Job represents the overall task, and is complete when there are .spec.completions successful Pods.
    - When using .spec.completionMode="Indexed", each Pod gets a different index in the range 0 to .spec.completions-1.
- Parallel Jobs w/ Work Queue:
    - Do not specify `.spec.completions`, default to `.spec.parallelism`.
    - The Pods must coordinate amongst themselves or an external service to determine what each should work on. For example, a Pod might fetch a batch of up to N items from the work queue.
    - Each Pod is independently capable of determining whether or not all its peers are done, and thus that the entire Job is done.
    - When any Pod from the Job terminates with success, no new Pods are created.
    - Once at least one Pod has terminated with success and all Pods are terminated, then the Job is completed with success.
    - Once any Pod has exited with success, no other Pod should still be doing any work for this task or writing any output. They should all be in the process of exiting.


??? example "Generating the YAML"

    === "Generating The Initial YAML"

        ``` yaml
        kubectl create job mynewjob --image=busybox --dry-run=client -o yaml -- sleep 5 > mynewjob.yaml
        ```


    === "mynewjob.yaml"


        ```yaml
        apiVersion: batch/v1
        kind: Job
        metadata:
        creationTimestamp: null
        name: mynewjob
        spec:
        completions: 3 # I Added this line 
        ttlSecondsAfterFinished: 60 # I Added this line
        template:
            metadata:
            creationTimestamp: null
            spec:
            containers:
            - command:
                - sleep
                - "5"
                image: busybox
                name: mynewjob
                resources: {}
            restartPolicy: Never
        status: {}
        ```




