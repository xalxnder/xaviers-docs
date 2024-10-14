---
title: 6.4 Restart Policy
---

restartPolicy determines what happens if a container, that is managed by a pod, crashes. Restart policy does not affect the state of the entire pod, though. If the Pod is stopped or killed, `restartPolicy=always` won't restart it