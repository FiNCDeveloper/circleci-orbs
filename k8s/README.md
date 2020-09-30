### publish development version

```
cd kustomize

DEV_VERSION=dev:new_feature

circleci orb validate ./orb.yaml
circleci orb publish ./orb.yaml finc/k8s@$DEV_VERSION
circleci orb info finc/k8s@$DEV_VERSION
```

### test

Your `.circleci/config.yml`

```yaml
orbs:
  kustomize: finc/k8s@dev:new_feature

# ... Use orb and test
```

### promote dev version

promote `dev:new_feature` version and bump patch version

```
circleci orb publish promote finc/kustomize@$DEV_VERSION patch
```

