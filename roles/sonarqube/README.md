# Atlassian Base

This playbook installs everything that all Atlassian applications need.
If it is duplicated, like the service file, it will be put here so that it is install everywhere.
This is also where the application installs since the difference is minimal.
Crowd is the special one, so we have if statements that look for crowd in the templates and does something special
