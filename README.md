# plugin-zabbix
Script para o monitoramento do número de usuários que estão utilizando o túnel.
Insira o 'script zabbix_plugin.sh' em um diretório (/etc/zabbix/scripts/, por exemplo). 

Depois altere a linha a seguir, que está presente em /etc/zabbix/zabbix_agentd.conf,

UserParameter=num_user.openvpn, cat /var/log/openvpn-status.log | sed -n '/Connected Since/,/ROUTING/p' | sed -e '1d' -e '$d' | wc

para
UserParameter=num_user.openvpn, ./etc/zabbix/scripts/zabbix_plugin.sh, cat /tmp/users.
