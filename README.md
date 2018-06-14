Tacacs+ Content pack for Graylog

Tested with Cisco

If you don't like to use whole content pack, just import the extractors for your Tacacs log input.


#### Linux config

vim /etc/tacacs+/tac_plus.conf

	accounting file = /var/log/tac_plus.acct

vim /etc/rsyslog.conf

	module(load="imfile" PollingInterval="1") #needs to be done just once

	# File 1
		
	input(type="imfile"
		
	File="/var/log/tac_plus.acct"
		
	Tag="tacacs-audit"
		
	Severity="info"
		
	Facility="local3")

	local3.* @<GRAYLOG-SERVER-IP/NAME:4949


