# marzban-zabbix

This template should be used only with a connection to [Marzban metric exporter](https://github.com/kutovoys/marzban-exporter). Follow the instruction to install this exporter firstly.

## Features
#### Item description
* marzban.get.metrics - collects all metrics from the Marzban host
* marzban.marzban_all_outgoing_bandwidth - collects all outgoing bandwidth
* marzban.marzban_all_incoming_bandwidth - collects all incoming bandwidth
* marzban.marzban_panel_users_active - collects active users amount
* marzban.marzban_panel_total_users - collects total users amount

#### Discovery description
* marzban.dynamic.monitoring.by.user - creates two item prototypes:
  * marzban.marzban_user_online[{#USERNAME}] - collects all the users and returns 0 (if the user offline) or 1 (if the user online)
  * marzban.marzban_user_used_traffic[{#USERNAME}] - collects all the user's outgoing traffic

## Configuration
### Requirements
* Zabbix server running on 7.0 version
* Installed [Marzban metric exporter](https://github.com/kutovoys/marzban-exporter) on a Marzban host
* Firewall rules that will allow Zabbix server connection to the Marzban host

### Installation
#### Template import
* Download one of the templates (they are all the same, just in different formats).
* Go into your Zabbix server -> Data collection -> Templates -> Import
* Choose your template and upload it
* Click **Import** button

#### Host configuration
* Go into your Zabbix server -> Data collection -> Hosts
* Choose your host and click on the name
* Go to Macros
* Add such variables there:

{$MARZBAN:IP} as a Macro and as a value type your Marzban server IP, where [marzban metric exporter](https://github.com/kutovoys/marzban-exporter) is installed
{$MARZBAN:METRICS_PORT} as a Macro and as a value type your Marzban exporter port (default: 9090)
(optional) {$MARZBAN:METRICS_PATH} as a Macro and as a value type your Marzban exporter metrics path (default: /metrics). Put this Macro only in case you did change path to the metrics

* Go back to the Host section
* In Template section start typing Marzban. You should choose this template and add it to the host
