# kubernetes-gitlab
Manifests to deploy GitLab on Kubernetes 

Installation process described in [blog](http://blog.lwolf.org/post/how-to-easily-deploy-gitlab-on-kubernetes/)

# Helm chart based on this manifests
[https://github.com/lwolf/gitlab-chart](https://github.com/lwolf/gitlab-chart)


## 2016-11-24 Update #1 after post was published

### Bump versions

* gitlab-runner:v1.8.0
* gitlab:8.16.3
* postgresql:9.5-3
* redis:3.2.4 (official redis container)

### Change in ingress

* SSH is now available through 22 service post.

# TL;DR

## Deploying GitLab itself
```
# create gitlab namespace
> $ kubectl create -f gitlab-ns.yml

# deploy redis
> $ kubectl create -f gitlab/redis-svc.yml
> $ kubectl create -f gitlab/redis-deployment.yml

# deploy postgres
> $ kubectl create -f gitlab/postgresql-svc.yml
> $ kubectl create -f gitlab/postgresql-deployment.yml

# deploy gitlab itself
> $ kubectl create -f gitlab/gitlab-svc.yml
> $ kubectl create -f gitlab/gitlab-svc-nodeport.yml
> $ kubectl create -f gitlab/gitlab-deployment.yml

```