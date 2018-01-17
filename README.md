# Canonical Distribution of Kubernetes with Monitoring

This is a bundle that includes CDK monitoring and loging. In this repo you will also find all needed scripts and templates required to have everything setup.

## Buidling and upgrading the bundle

Deploying CDK using this bundle is not advised. You should be deploying CDK with Conjure-up so you get the latest stable release with all its monitoring facilities. In case this is not an option here is how you can rebuild/update the bundle found on this project.

First get the latest CDK bundle from the bundle. Lets start our work on CD with canal

```
> charm pull canonical-kubernetes-canal
```

Logging and monitoring is added ontop of CDK in conjure-up. For both logging and monitoring you would need to grab bundle.yaml additions and mergethem manualy, you should also update the templates used eg for dashboards and update the init-mon-and-log script.

### Adding logging and monitoring

- Grab the bunlde.yaml from here: https://github.com/conjure-up/spells/tree/master/canonical-kubernetes/addons/graylog and merge it to the bundle.yaml you got with `charm pull` above. 

- Go over the after deploy script: https://github.com/conjure-up/spells/blob/master/canonical-kubernetes/addons/graylog/steps/01_install-graylog/after-deploy and make sure you refactor the `init-mon-and-log.sh` script goes through the same steps.

- Copy under templates any template files referenced in the above script and make sure you reference them corectly.

- Repeat the above steps for Monitoring https://github.com/conjure-up/spells/tree/master/canonical-kubernetes/addons/prometheus

