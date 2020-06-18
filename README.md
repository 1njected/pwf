# Proxy WAF

Build nginx from source with modsecurity:
https://github.com/SpiderLabs/ModSecurity-nginx


Copy/git clone pwf-folder to /opt/
	
	git clone --recurse-submodules https://github.com/1njected/pwf


Copy etc_nginx_confd/proxywaf.conf to /etc/nginx/conf.d/

Adjust config as needed regarding certifcates, DNS lookup, etc.


Files:
	
	modsec.conf - main modsecurity config that nginx loads.
	modsecurity.conf - Modsecurity generic configuration
	custom.conf - custom rules should be applied here
	disabled.conf - disable rules here

Directories:
	
	tls/ 		- certificates used by nginx
	wwwerr/		- error/deny page
	uploads/ 	- Files posted/uploaded gets saved here
	crs/		- Modsecurity Core Rule Set - update can be applied from https://github.com/coreruleset/coreruleset

lists/
	
	bl_args 		- Block HTTP Get Args http://srv/test.php?blockthis
	
	bl_ip / wl_ip 		- White/Black list IP
	
	webshells-ssdeep.txt 	- Block webshells using ssdeep signatures 
	

Reload config:
	
	nginx -s reload

Log:
	
	SecAuditLog /var/log/modsec_audit.log - see modsecurity.conf


