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

### Migrating from v1 to v2

Upgrading to v2 from v1 is not much of a change except one command rename.

Here's complete upgrade guide.

#### 1. Upgrade to the latest orb

```diff
orbs:
- finc-k8s: finc/k8s@1.0.0
+ finc-k8s: finc/k8s@2.0.0
```

#### 2. (Important) rename `update-container-images` command if you use.

`update-container-images` is renamed to `update-deployment-images` in v2 to express what command does more explicitly.

Only command rename is neccessary, everything else is the same.

```diff
steps;
-  - finc-k8s/update-container-images:
+  - finc-k8s/update-deployment-images:
      container-image-updates: your-container-image:latest
      namespace: awsome-app
      watch-timeout: 5m
      deployment-target: stable
```

#### 3. (New feature) add command to update cronjob image if necessary.

v2 has a feature to update cronjob images like deployment. If you app has any cronjobs then you can use `update-cronjob-images` command to update all the cronjob images.

```diff
steps:
  - finc-k8s/update-deployment-images:
      container-image-updates: your-container-image:latest
      namespace: awsome-app
      watch-timeout: 5m
      deployment-target: stable
+ - finc-k8s/update-cronjob-images:
+     container-image-updates: your-container-image:latest
+     namespace: awesome-app
```

And that's it!

If you neet to know more, then please see the full change log [here](https://github.com/FiNCDeveloper/circleci-orbs/blob/master/k8s/CHANGELOG.md#200---2021-06-14) or the [document](https://circleci.com/developer/orbs/orb/finc/k8s).
