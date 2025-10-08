# Flux-CD How to Guide

There is alot to explain with flux but it is easily to get the hang of with the use of youtube.

Per my configuration Helm charts are pinned to a version and not updated by Flux until I can figure out how to setup auto PRs for updates, as I dont want it updating on its own. But any standalone deployments with the weird comment next to the image version are maintained by flux-cd. Flux scans the repository and if a new version is available it will update, push to a new branch, and create a PR. This way all you have to do to update standalone deployments is to merge the PR and watch the Pod recreate.
