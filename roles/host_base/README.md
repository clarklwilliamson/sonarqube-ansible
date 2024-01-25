# host_base role and what it does

## This playbook does the following

1. Sets the root password to expire after 5 years
2. Configures rpm-local repository
3. Configures epel-release repository
4. Configures dnf to include the kernel and only install 2 versions.
5. Installs and configures nagios, We don't want monitoring just yet, though
6. Installs dynatrace with csg tennant ID (Right now we don't have enough licenses.)
7. Disables unused repos.

    Our images by default come with jboss enabled, since its an RedHat/IBM product.

    These repositorys are disabled:
    - rhel-8-x86_64-appstream
    - rhel-8-x86_64-jb-coreservices-1
    - rhel-8-x86_64-jb-eap-7.3
    - rhel-8-x86_64-jws-5

    Appstream takes precidence but we don't install anything from there.

    The Appstream repository includes PostgreSQL, nginx, and a few other tools we use.

    We can't install our software if Appstream is present.

## how to add and extend roles

Because we use a top level design, you will want to add your role to the group in applications.yml

In the roles, we don't have to declare tasks since we put them in tasks/main.yml, it assumes they are tasks
