---
title: "GCP CLI Cheatsheet"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
date: 2022-11-12 18:09:02 UTC
---

## Retrieve project owner info

```bash
# gcloud projects list - list projects accessible by the active account
# Lists all active projects, where the active account has Owner, Editor,
#    Browser or Viewer permissions. Projects are listed in alphabetical order by
#    project name. Projects that have been deleted or are pending deletion are
#    not included.
gcloud projects list --sort-by=projectId --limit=5
gcloud projects list --filter='lifecycleState:DELETE_REQUESTED'

# retrieve project owners
gcloud projects get-iam-policy $PROJECT_ID --flatten=bindings --filter=bindings.role:roles/owner --format='value(bindings.members)'

# retrieve project creator
gcloud logging read --project $PROJECT_ID --order=asc --limit=1 --format='table(protoPayload.methodName, protoPayload.authenticationInfo.principalEmail)'
```
