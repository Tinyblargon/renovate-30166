# 30166

## Current behavior

In `requirements.ansible.yml` Renovate is unable to update `Tinyblargon.docker_deploy` due to it being in 2 namespaces.

It can update `Tinyblargon.certbot` can updated without issue.

### Why this is happening

In the past the old ansible galaxy server would force a username to lowercase. This was changed in the new galaxy server to allow for case sensitive usernames.
My username is mixed case so everything i've uploaded in the past was put in the old [tinyblargon](https://galaxy.ansible.com/ui/standalone/namespaces/9993/) namespace.
Everything i've uploaded since the change has been put in the mew [Tinyblargon](https://galaxy.ansible.com/ui/standalone/namespaces/6988/) namespace.

This has the effect that roles that were uploaded before the change are in the old `tinyblargon` namespace and roles uploaded after the change are in the new `Tinyblargon` namespace.
Roles in the old `tinyblargon` namespace that where updated after the change are in both namespaces.

On ansible galaxy the have fixed this by effectively merging the two namespaces. This is why you can see the same role in two different namespaces.

- https://galaxy.ansible.com/ui/standalone/roles/Tinyblargon/docker_deploy/
- https://galaxy.ansible.com/ui/standalone/roles/tinyblargon/docker_deploy/

## Expected behavior

Renovate treating `Tinyblargon.docker_deploy` and `tinyblargon.docker_deploy` as the same role and updating it.

## Link to the Renovate issue or Discussion

proposed solution in discussion: https://github.com/renovatebot/renovate/discussions/30166
