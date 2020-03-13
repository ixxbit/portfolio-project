---
description: Docker
---

# Providing Consistent App Environments

## Problem Statement

Favorable environment: where the tree is being watered and nourished in an adequate environment the it grows healthy and strong because all all dependencies and requirements are providing throughout its life time as it continues to grow.

Unfit environment: the required dependencies for growing the tree not present then the tree will die.

![](../../../.gitbook/assets/image%20%2833%29.png)



When application runs on an inconsistent environment that doesn't support the application dependencies, then the app will fail.

![](../../../.gitbook/assets/image%20%2883%29.png)

* Say the application passed when tested on the Test server, however it failed when deployed on the Production Server

## Solution Approach

1. Create a Microservice based application
2. Build it on Jenkins Server
3. Deploy and maintain the application using it docker

 iteploy an application using docker

![](../../../.gitbook/assets/image%20%28118%29.png)

* Each microservice is defined by a Dockerfile 

## Solution Steps

{% embed url="https://youtu.be/hMlr1KlazBk?t=1241" %}



