---
title: 6.6 Cron Jobs
---

A Cron Job adds a schedule to a job. 


??? example "Cronjobs"

    === "Cronjob Example"

        ``` bash
        kubectl create cronjob runme --image=busybox --schedule="*/2 * * * *" -- echo greetings from the cluster
        ```


    === "Explanation"
        
        The following creates a cron job, named `runme`,  that runs every 2 minutes. It uses the busybox image and echos "greetings from the cluster"


### Testing 
Lets say you have a cronjob that only runs once a week, but you want to test it now. You can test your cronjobs like  this: `kubectl create job {name-of-job} --from=cronjob/{name-of-job}`. 