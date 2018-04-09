+++
date = "2018-01-05T00:00:00"
description = "Validate Kubernetes yaml files online!"
thumbnail = "images/kubeval_online.png"
image = "images/kubeval_online.png"
title = "Kubeval Online"
slug = "kubeval-online"
author = "Shaun Donachy"
draft = false
hidesidebar = true
+++

### Validate Kubernetes (k8s) yaml files online.
This project was inspired by and based on [garethr's kubeval](https://github.com/garethr/kubeval). After attending his talk at Kubecon in December 2017 I put this together to make use of kubeval to perform validations by pasting into a web interface. Garethr's kubeval already has a nice CLI you can use as part of a CI/CD system, and kubevalonline supplements this tool for use during the development process.

Given a kubernetes configuration file with an invalid value such as:
``` json
apiVersion: v1
kind: Service
metadata:
  name: redis-master
  labels:
    app: redis
    tier: backend
    role: master
spec:
  ports:
    # the port that this service should serve on
  - port: sds
    targetPort: 6379
  selector:
    app: redis
    tier: backend
    role: master
```
kubeval recognizes that port values should be integer type and not string type then responds with an error:
``` json
{
  "Results": [
    {
      "Kind": "Service",
      "Success": false,
      "Errors": [
        "Invalid type. Expected: integer, given: string"
      ]
    }
  ]
}
```

`kubectl run` provides a `--dry-run` flag which can also be used to partially verify that a declaration is valid, but kubeval provides additional information that is valuable when debugging. A handy tool for the kubernaut!

The source code is hosted on [github](https://github.com/donachys/kubevalonline). The image can be pulled from [dockerhub](https://hub.docker.com/r/donachys/kubevalonline/).

[Travis CI](https://travis-ci.org/donachys/kubevalonline) and [coveralls](https://coveralls.io/github/donachys/kubevalonline?branch=master) handle the build and code coverage.
[![Build Status](https://travis-ci.org/donachys/kubevalonline.svg?branch=master)](https://travis-ci.org/donachys/kubevalonline) [![Coverage Status](https://coveralls.io/repos/github/donachys/kubevalonline/badge.svg?branch=master)](https://coveralls.io/github/donachys/kubevalonline?branch=master)