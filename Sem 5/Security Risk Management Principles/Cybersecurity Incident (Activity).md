#SRMP 
The College's Student Info System may have experienced unauthorized access. The security team has collected four different types of data. Each group will investigate one dataset
We are group B
Group B: Firewall Logs
TIME      SOURCE IP       DESTINATION        PORT     ACTION
----------------------------------------------------------------
10:02           10.10.5.20           Web Server                 443      ALLOW
10:05           10.10.5.21           Web Server         443      ALLOW
10:17           185.44.x.x           Web Server         443      ALLOW
10:18           185.44.x.x           Web Server         443      ALLOW
10:19           185.44.x.x           Database Server    3306     DENY
10:20           185.44.x.x           Database Server    3306     DENY
10:21           185.44.x.x           Web Server         443      ALLOW
10:22           Web Server           External IP        443      ALLOW
10:23           Web Server           External IP        443      ALLOW
10:24           Web Server           External IP        443      ALLOW
