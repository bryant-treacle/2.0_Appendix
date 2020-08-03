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


   
   



.. warning::

   Security Onion 2.0 is a MAJOR architectural change, so please note the following:

   - Security Onion 2.0 has higher hardware requirements, so you should check that your hardware meets those requirements. 
   - Once you've upgraded from Ubuntu 16.04 to Ubuntu 18.04, you will essentially do a new installation of Security Onion 2.0 on top of Ubuntu 18.04.  Very little data will be retained during the upgrade!
   - There will be no way to migrate application accounts from 16.04 to 2.0.
   - There will be no way to migrate sguild data from 16.04 to 2.0.
   - You may need to purge pcap to make free space for the upgrade process. Any pcap remaining after the upgrade can only be accessed via tcpdump.
   - We do not provide any guarantees that the upgrade process will work! If the upgrade fails, be prepared to perform a fresh installation of Security Onion 2.0.
 
For the reasons listed above, we recommend that most users procure new hardware and perform a fresh installation of Security Onion 2.0.

.. tip::

   If you're planning to purchase new hardware, please consider official Security Onion appliances from Security Onion Solutions (https://securityonionsolutions.com). Our custom appliances have already been designed for certain roles and traffic levels and have Security Onion pre-installed. Purchasing from Security Onion Solutions will save you time and effort **and** help to support development of Security Onion as a free and open source platform!

If you have reviewed all of the warnings above and still want to attempt an in-place upgrade, you should be able to do the following:

 - perform an in-place upgrade from Ubuntu 16.04 to Ubuntu 18.04 using standard Ubuntu procedures
 - once you have completed the Ubuntu 18.04 upgrade, follow the Ubuntu 18.04 instructions in the Installation Guide
