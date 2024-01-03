# ansible_role_psql_client_pod

[![Validate infrastructure as code](https://github.com/garliclabs/ansible_role_psql_client_pod/actions/workflows/validation.yml/badge.svg)](https://github.com/garliclabs/ansible_role_psql_client_pod/actions/workflows/validation.yml)

You can give this pod a list of sql queries, they will be executed against a postgres database that is running inside your kubernetes.  
The idea of this pod is mainly to use it for automation of postgres database tasks.  

## Role Variables

```yaml
psql_client_state: present
psql_postgres_host: postgresql.default.svc.cluster.local
psql_postgres_username: "{{ undef(hint='Specify the username to connect with a postgres database') }}"
psql_postgres_user_password: "{{ undef(hint='Specify the password for the database user') }}"
psql_namespace: default
psql_queries: 
  - ""
psql_just_run: false
```

**psql_client_state:** State of the pod, usally `present`, if you want to destroy the running pod you can set it to `absent`
**psql_postgres_host:** Kubernetes hostname of the postgres database
**psql_postgres_username:**  Username used to connect to the database
**psql_postgres_user_password:**  Password of the user that is used to connect to the database
**psql_namespace:**  Namespace where the pod should be started
**psql_queries:** Define a list of sql queries that should be executed against the configured database 
**psql_just_run:** If true the pod will be destroyed after a successfull run, else it will stay so you are able to exec in to it.  

## Dependencies

None.

## License

GNU General Public License version 3

## Development

### Linting & static security analyser

Both the linter and the static security analyser are running on each push on the github actions pipeline.  

* As linter [ansible-lint](https://ansible.readthedocs.io/projects/lint/) is used. For installation documentation see [ansible lint installing](https://ansible.readthedocs.io/projects/lint/)
  * Just run `ansible-lint`

* To check if there are any passwords, tokens... hardcoded, [kics](https://kics.io/index.html) is used to ensure a secure IaC repository.  
  * Run it locally `docker run -t -v $PWD:/path checkmarx/kics:latest scan -p /path -o "/path/"`
