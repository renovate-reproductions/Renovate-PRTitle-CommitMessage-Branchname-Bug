# Renovate PR Title bug

Given a repository with the structure:

```
root
—{{project_template}}/Pipfile
—project_template/Pipfile
.renovaterc.json
```
and upgrading packages using the `Pipfile` in `{{project_template}}` and `project_template`,
and the relevant configuration parameters in `renovaterc.json` are set like:

```
"packageRules": [
    {
    "groupName": "\\{{parentDir}}",
    "matchPackagePatterns": [".*"]
    }]
```

The expect PR has the following properties:

```
PR Title 1 = “TicketID {{project_template}}: Upgrade depedencies” 

PR Title 2 = “TicketID project_template: Upgrade dependencies” 
```

The actual PR has the following properties: 

```
PR Title 1 = “TicketID : Upgrade” 

PR Title 2 = “TicketID project_template: Upgrade dependencies” 
```

Hence, the expected `PR Title 1` is different than the actual `PR Title 1`. 
`PR Title 2` is handled correctly.
