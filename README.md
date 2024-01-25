# Top Level Read Me

## How to use this setup

Environments controls the vars for the groups.

Environments folder contains production and staging.

the applications.yml and database.yml control the roles for each group of servers.

if you want to add a role to a group this is where you add it.

if you want to add another class of servers, you create the application.yml file, and then add it site.yml

## Prep for upgrades

Download the application, modify it as needed, and upload it to artifactory staging in the largefile repo.

