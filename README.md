Tacacs+ Content pack for Graylog

Tested with Cisco


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

#### TODO

1) Move from "Split & Index" to "Grok" patterns.
