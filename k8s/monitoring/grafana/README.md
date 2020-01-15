Grafana
=======

Our grafana set up consists of

* 1 [Deployment][1] with
* 3 ConfigMaps.

The three configMaps are:

* [Dashboard location][1] - This point out the mount point the [Dashboard Definitions][11].
* [Dashboard Definitions][11] - Dashboards taken from Grafana.com
* [Datasource definitions][12] - Defines the connection to our [Prometheus](../prometheus) deployment.


How to view Grafana:
--------------------
To access the Grafana dashboards one first needs to run
```bash
kubectl port-forward service/grafana 3000 -n monitoring
```
and then go to [localhost:3000](http://localhost:3000).
Log in is `admin:admin`.

How to add dashboards:
---------------------
If you find a dashboard on grafana.com that you like to add copy the dashboard ID and run:
```bash
bin/add_grafana_dashboard.py
```
This will prompt you for the Id and any template variables present in the dashboard.

[1]: deployment.yml
[11]: dashboard-definitions.yml
[12]: datasources.yml

