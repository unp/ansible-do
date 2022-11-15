## Ansible install

- Expects Ubuntu hosts

These playbooks deploy my desired software. To use, edit the `hosts` file to include the names or URLs of the servers you want to deploy.

# Download external roles
```
    ansible-galaxy install geerlingguy.security
    ansible-galaxy install oefenweb.fail2ban
    ansible-galaxy collection install community.general
    ansible-galaxy collection install community.docker
    ansible-galaxy install nickjj.docker
```

Now you can run the playbooks!

# Playbooks

## 1) Harden your ssh proxy box
This playbook is meant to be run only once on a new box. This code is likely not going to be changed very often and it takes a bit of time to complete. For this reason I generally just run it once on a new machine, then only run the deploy command in the future. If this base install code ever changes I generally just migrate to a new box anyways.

    ansible-playbook -i hosts.yaml base.yml

## 2) Update application
This runs the main deploy code. It will make sure your software is provisioned correctly and update and restart the docker containers running the services. This is what you will run to deploy your software every time.

    ansible-playbook -i hosts.yaml app1.yml
