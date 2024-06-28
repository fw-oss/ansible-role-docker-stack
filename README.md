# Role Name

Set up [portainer](https://docs.portainer.io/), [traefik](https://doc.traefik.io/traefik/) and [watchtower](https://containrrr.dev/watchtower/) in docker

## Requirements

Docker up and running

## Role Variables

tbd  

- docker_logins
    - docker_registry_url
    - docker_registry_user
    - docker_registry_pass
- docker_traefik_metrics bool
- docker_traefik_metrics_port number 
- docker_traefik_metrics_external bool external erreichbar
- docker_traefik_metrics_network
- docker_traefik_additional_entrypoints 
  - name
  - port
  - protocol
- docker_traefik_non_docker_services
  - name
  - routs []
    - url
    - middlewares
  - servers []
  - traefik_default_networks []
  - docker_traefik_certs_crt_file
  - docker_traefik_certs_key_file
- docker_traefik_basic_auth
- docker_traefik_default_ipwhitelist []
- docker_traefik_basic_auth []
- docker_traefik_root_url

- docker_portainer_root_url
- docker_portainer_parameter
  watchtower_schedule: "0 0 22 * * *" # trumpft poll
Check if file '/root/.docker/config.json' exists.

- watchtower_notification_service (email, shoutrrr)
- watchtower_notification_email_from
- watchtower_notification_email_to
- watchtower_notification_email_server
- watchtower_notification_email_server_port
- watchtower_notification_email_server_user
- watchtower_notification_email_server_password
- watchtower_notification_email_delay

- watchtower_notification_url

## Dependencies

[Community General Collection](https://docs.ansible.com/ansible/latest/collections/community/general/index.html) (comes with `ansible`, but not with `ansible-core`)

## Example Playbook

Depending on what loadout you wanna achieve:

```yaml
    - name: Install Stack on Docker host
    - hosts: docker
      become: true
      vars:
        docker_install_traefik: true
        docker_install_watchtower: false
        docker_install_portainer: true
        docker_install_portainer_agent: false
      roles:
        - ansible_role_docker_stack
```
```yaml
    - name: Install traefik with wildcard certificates on Docker host
    - hosts: docker
      become: true
      vars:
        docker_install_traefik: true
        # TODO 
      roles:
        - ansible_role_docker_stack
```
```yaml
    - name: ...
```

## License

MIT

## Author Information

FW-OSS, 2024

## Todos
- Documentation
- Tests
- Treafik Wildcard Merge
- Linting
- toggle docker_traefik_force_restart


