.. _appendix:

Appendix A: Grafana Lab
========
Task 1: Create a Grafana Dashboard and Panel
   - In the Grafana Web console, hover over the dashboard icon and select: ``Manage``
   - In the ``Manage dashboard & folders`` page, select: ``New Dashboard``
   - In the ``New Dashboard`` page, select: ``Add new Panel``
   - In the query tab, select: ``InfluxDB``
   - Under the ``A`` dropdown choose the following options:
      - FROM:
         - Click ``select measurement`` and select: ``net``
         - Click the ``+`` and select: ``host``
         - Click ``select tag value`` and select: ``so-sensor01``
         - Click the ``+`` and select: ``interface``
         - Click ``select tag value`` and select: ``bond0``

      - SELECT:
         - Click ``field value`` and select: ``bytes_recv``
         - Click the ``+`` and select: ``derivative`` under the transformations dropdown and set the value to ``1s``
         - Click the ``+`` and select: ``math`` and set the value to ``(*8)``
      
      - ALIAS BY:
         - Query Alias: ``Inbound Bytes``
         
   - Click on the ``Save`` icon located on the top right of the page and save the new dashboard with the following settings:
      - Dashboard Name: ``Alerting Dashboard``
      - Under the ``Folder`` dropdown, select: ``General``
      - Click: ``Save``
Task 2: Add a new email notifications channel in Grafana
   - In the Grafana Web console, hover over the Alerting icon and select: ``Notification Channel``
   - In the ``Alert rules & notification`` page, select: ``Add channel``
   - Use the following settings to configure the Email Notification channel:
      - Name: ``Tech Support``
      - Type: ``Email``
      - Addresses:``tech-support@pwned-corp.com;mike@pwned-corp.com;management@pwned-corp.com`` 
   - Click: ``Save``

Task 3: Configure Alerting on the InBound Bytes Panel
   - In the Grafana Web console, hover over the ``Dashboard`` icon and select: ``Manage``
   - Click on the ``General`` dropdown and select: ``Alerting Dashboard``
   - Click on the panel you created and select: ``Edit``
   - Click on the ``Alert`` tab and select: ``Create Alert``
   - Use the below settings to configure the rule:
      - Name: ``so-forward Interface Alert``
      - Evaluate every: ``1m``
      - For: ``10m``
      - Conditions:
         - WHEN: ``count() OF query(A, 5m, now) IS BELOW 1``
      - Notifications:
         - Send to: ``Tech Support``
         - Message: ``No span traffic seen on so-sensor01 in the last 10 minutes.``
   - On the top right corner of the page, click: ``Save``

   
   



