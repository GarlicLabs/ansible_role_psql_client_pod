ansible_role_psql_client_pod
=========

You can give this pod a list of sql queries, they will be executed against a postgres database that is running inside your kubernetes.  
The idea of this pod is mainly to use it for automation of postgres database tasks.  

Role Variables
--------------

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
