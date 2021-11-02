# Renovate PR Title, CommitMessage and Branchname bug

Given a repository with the structure:
```
root
—{{project_template}}/Pipfile
.renovaterc.json
```

and upgrading packages using the `Pipfile` in `{{project_template}}`
and the relevant configuration parameters in `renovaterc.json` are set like:

```
"additionalBranchPrefix": "{{parentDir}}-",
"commitMessagePrefix": “TicketID- {{parentDir}}:",
```

The expect PR has the following properties:

PR Title = “TicketID {{project_template}}: Upgrade {{Project_Name}}” 
commit message = “TicketID {{project_template}}: Upgrade dependency `package` to `new_version`” 
branch name = renovate/{{project_name}}-parentdir


The actual PR has the following properties: PR Title = “TicketID: Upgrade” 
commit message = “TicketID: Upgrade dependency” 
branch name = renovate/-parentdir

