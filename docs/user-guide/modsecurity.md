# ModSecurity Web Application Firewall

ModSecurity is an open source, cross platform web application firewall (WAF) engine for Apache, IIS and Nginx that is developed by Trustwave's SpiderLabs. It has a robust event-based programming language which provides protection from a range of attacks against web applications and allows for HTTP traffic monitoring, logging and real-time analysis - https://www.modsecurity.org

The [ModSecurity-nginx](https://github.com/SpiderLabs/ModSecurity-nginx) connector is the connection point between NGINX and libmodsecurity (ModSecurity v3).

The default ModSecurity configuration file is located in `/etc/nginx/modsecurity/modsecurity.conf`. This is the only file located in this directory and contains the default recommended configuration. Using a volume we can replace this file with the desired configuration.
To enable the ModSecurity feature we need to specify `enable-modsecurity: "true"` in the configuration configmap.

**NOTE:** the default configuration use detection only, because that minimises the chances of post-installation disruption.
The file `/var/log/modsec_audit.log` contains the log of ModSecurity.


The OWASP ModSecurity Core Rule Set (CRS) is a set of generic attack detection rules for use with ModSecurity or compatible web application firewalls. The CRS aims to protect web applications from a wide range of attacks, including the OWASP Top Ten, with a minimum of false alerts.
The directory `/etc/nginx/owasp-modsecurity-crs` contains the https://github.com/SpiderLabs/owasp-modsecurity-crs repository.
Using `enable-owasp-modsecurity-crs: "true"` we enable the use of the rules.
