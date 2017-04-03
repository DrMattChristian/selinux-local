# Check for AVR denied as root:

```
# grep -i denied /var/log/audit/audit.log | audit2why
# grep -i nagios /var/log/audit/audit.log | audit2allow -m local-nagios
```

# Edit .te file:

```
$ vim local-nagios.te
```

# Update version number. Then check and compile:

```
checkmodule -m -o local-nagios.mod local-nagios.te
semodule_package -o local-nagios.pp -m local-nagios.mod
```

# Install as root:

```
semodule -i local-nagios.pp
semodule -l | grep -i nagios
```
