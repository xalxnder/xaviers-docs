---
title: 6.2 Sidecar Container
---
A sidecar container is an initContainer that has a restartPolicy set to Always. There is no "sidecar" container property. To create one just create an initContainer with the restartPolicy set to Always. Like a regular initContainer, the sidecar must complete once before the main Pod is started.