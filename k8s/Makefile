####
# Circleci finc/k8s orb release script
###

ORB_COMMAND=circleci orb
ORB_NAME=finc/k8s
DEV_VERSION=dev0.1
DEV_FULL_VERSION=$(ORB_NAME)@dev:$(DEV_VERSION)

# major, minor, patch
BUMP_TARGET=patch

dev-publish: orb.yaml
	$(ORB_COMMAND) validate $<
	$(ORB_COMMAND) publish  $< $(DEV_FULL_VERSION)
	$(ORB_COMMAND) info $(DEV_FULL_VERSION)

promote-from-dev:
	$(ORB_COMMAND) publish promote $(DEV_FULL_VERSION) $(BUMP_TARGET)

