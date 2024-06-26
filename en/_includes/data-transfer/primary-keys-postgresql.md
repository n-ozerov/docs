To transfer tables without primary keys for the _{{ dt-type-repl }}_ and _{{ dt-type-copy-repl }}_ transfer types, you must add the `REPLICA IDENTITY`:

* Do not transfer tables without primary keys. For this purpose, add them to the list of excluded tables in [source endpoint settings](../../data-transfer/operations/endpoint/source/postgresql.md#additional-settings.md).
* Add the replica ID to tables without `primary keys`:
   * For tables with an index, set `REPLICA IDENTITY` by `unique key`:

      ```sql
      ALTER TABLE MY_TBL REPLICA IDENTITY USING INDEX MY_IDX;
      ```

   * For tables without an index, change `REPLICA IDENTITY`:

      ```sql
      ALTER TABLE MY_TBL REPLICA IDENTITY FULL;
      ```
      In this case, {{ data-transfer-name }} will treat such tables as tables where the primary key is a composite key that includes all columns of the table.

If there are no primary keys in a table, logical replication [will not include any changes in the rows]({{ pg-docs }}/logical-replication-publication.html) (`UPDATE` or `DELETE`).

* If, while trying to transfer tables from {{ PG }} to {{ PG }}, you do not exclude a table without primary keys on the transfer source, the following error message will be returned:

   ```text
    failed to run (abstract1 source): Cannot parse logical replication message: failed to reload schema: primary key check failed: Tables: n / N check failed: "public"."MY_TBL": no key columns found
   ```

* If, while trying to transfer tables from {{ PG }} to a different database, you add a table without primary keys, the following error message will be returned:

   ```text
   failed to run (abstract1 source): Cannot parse logical replication message: failed to reload schema: primary key check failed: Tables: n / N check failed:
   "public"."MY_TBL": no key columns found
   ```
