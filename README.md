# network-security-threat-research
Akamai Network Security Threat Research  

## akarank-workflow  

akarank-workflow runs daily at 10am UTC and commits latest produced akarank output ```top10K.csv``` to main branch.  

The commited file is downloaded as blob from:  
```
storageaccount: raddeakarankstorage  
container: output-top-n  
date: workflow execution day - 1 day
file: top10K.csv  
```

## Important Notes
- akarank-workflow uses Personal Access Token (PAT) to automerge to main. PAT has fixed expiration date  
- automerge action details https://github.com/marketplace/actions/auto-merge-pull-request  
- using GITHUB_TOKEN when triggering other actions with github action auto-pull-request:  
> "Pull requests created by the action using the default GITHUB_TOKEN cannot trigger other workflows. If you have on: pull_request or on: push workflows acting as checks on pull requests, they will not run."  

sources:  
    - https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#triggering-further-workflow-runs  
    - https://github.com/peter-evans/create-pull-request/issues/48  
