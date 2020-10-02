####
# Circleci finc/kustomize orb release script
###
ORB_COMMAND=circleci orb
ORB_NAME=finc/kustomize
DEV_VERSION=dev0.2
DEV_FULL_VERSION=$(ORB_NAME)@dev:$(DEV_VERSION)

BUMP_TARGET=patch # major, minor, patch

dev-publish: orb.yaml
	$(ORB_COMMAND) validate $<
	$(ORB_COMMAND) publish  $< $(DEV_FULL_VERSION)
	$(ORB_COMMAND) info $(DEV_FULL_VERSION)

promote-from-dev:
	$(ORB_COMMAND) publish promote $(DEV_FULL_VERSION) $(BUMP_TARGET)


