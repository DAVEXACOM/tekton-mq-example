FROM ibm-mqadvanced-server-integration:9.1.3.0-r4-amd64

USER mqm

COPY TLSPRQM1.mqsc /etc/mqm/
COPY NOTLS.mqsc /etc/mqm/
COPY MYDEFS.mqsc /etc/mqm

COPY TLSPRQM1.kdb /etc/mqm/
COPY TLSPRQM1.crt /etc/mqm/
COPY TLSPRQM1.rdb /etc/mqm/
COPY TLSPRQM1.sth /etc/mqm/