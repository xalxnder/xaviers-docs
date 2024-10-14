---
title: 6.3 Port Forwarding
---

A very simple way to expose a Pod port on the kubectl host (your workstation) that forwards to the pod This is useful for TESTING Pod accessibility on a specific cluster node, not to expose it to external users. For example, if you want to verify that a pod is doing what it should be doing. In a live enviornment, you should use services or ingress.

```bash
[xavier@xa-dev-main ~]$ kubectl run fwnginx --image=nginx
pod/fwnginx created
[xavier@xa-dev-main ~]$ kubectl port-forward fwnginx 8080:80 &
[1] 2609368
[xavier@xa-dev-main ~]$ Forwarding from 127.0.0.1:8080 -> 80
Forwarding from [::1]:8080 -> 80

[xavier@xa-dev-main ~]$ curl localhost:8080
Handling connection for 8080
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

```