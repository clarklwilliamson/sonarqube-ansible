# Top Level Read Me

## How to use this setup

Environments controls the vars for the groups.

Environments folder contains production and staging.

the applications.yml and database.yml control the roles for each group of servers.

if you want to add a role to a group this is where you add it.

if you want to add another class of servers, you create the application.yml file, and then add it site.yml

## Prep for upgrades

Download the application, modify it as needed, and upload it to artifactory staging in the largefile repo.

## Jira

1. Rename the zip to jira-software-version.tar.gz
2. Put all the files in the root.
3. [Jira playbook README](/roles/jira/README)

## Confluence

1. Put all the files in the root.
2. [Confluence playbook README](/roles/confluence/README)

## Crowd

1. Put all the files in the root.
2. [Crowd playbook README](/roles/crowd/README)

## Upgrading the installed version

Change the version number in the environment you want to update, for example.

[Environments README](/environments/README)

Go to Environments -> staging -> jira.yml and change application_version to the version you want to upgrade to.

Run the playbook.

Manually stop the application on each server, change the link in /apps/atlassian/ to the new version, start the application.

## Tags

I have one tag, update which needs to be declared explicitly because I want to test rebooting the server after the packages are upgraded.

Although I do have a rule not to have reboot in a playbook, it might be something I figure out.


## Files
confluence.cfg.xml has the IPS for the cluster

If you take the db from production, run this:
```
    delete from clusternode where node_id = '833';
    delete from clusternodeheartbeat where node_id = '833';
    delete from replicatedindexoperation where node_id = '833';
    delete from clusternode where node_id = '843';
    delete from clusternodeheartbeat where node_id = '843';
    delete from replicatedindexoperation where node_id = '843';
    delete from clusternode where node_id = '844';
    delete from clusternodeheartbeat where node_id = '844';
    delete from replicatedindexoperation where node_id = '844';
```

Also if you change versions, the new version might have a db upgrade, and it will cause issues.

You can copy plugins from staging to prod for both confluence and jira.