### publish development version

```
cd kustomize

DEV_VERSION=awesome_command

circleci orb validate ./orb.yaml
circleci orb publish ./orb.yaml finc/kustomize@dev:$DEV_VERSION
circleci orb info finc/kustomize@dev:$DEV_VERSION
```

### test

Your `.circleci/config.yml`

```yaml
orbs:
  kustomize: finc/kustomize@dev:awesome_command

# ... Use orb and test
```


### promote dev version

promote `dev:awesome_command` version and bump patch version

```
circleci orb publish promote finc/kustomize@dev:awesome_command patch
```

