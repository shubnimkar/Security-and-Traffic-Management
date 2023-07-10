# Basic Commands:
    firewall-cmd --state: Check the status of Firewalld.
    firewall-cmd --get-default-zone: View the default zone.
    firewall-cmd --get-active-zones: List the active zones.
    firewall-cmd --get-zones: List all available zones.

# Zone Management:
    firewall-cmd --get-default-zone: View the default zone.
    firewall-cmd --set-default-zone=<zone>: Set the default zone.
    firewall-cmd --get-zone=<zone>: View information about a specific zone.
    firewall-cmd --list-all-zones: List all zones and their configuration.
    firewall-cmd --zone=<zone> --add-interface=<interface>: Add an interface to a zone.
    firewall-cmd --zone=<zone> --change-interface=<interface>: Change the interface of a zone.
    firewall-cmd --zone=<zone> --remove-interface=<interface>: Remove an interface from a zone.

# Service Management:
    firewall-cmd --get-services: List all available services.
    firewall-cmd --zone=<zone> --add-service=<service>: Add a service to a zone.
    firewall-cmd --zone=<zone> --remove-service=<service>: Remove a service from a zone.
    firewall-cmd --zone=<zone> --list-services: List services allowed in a zone.

# Port Management:
    firewall-cmd --zone=<zone> --add-port=<port>/<protocol>: Add a port to a zone.
    firewall-cmd --zone=<zone> --remove-port=<port>/<protocol>: Remove a port from a zone.
    firewall-cmd --zone=<zone> --list-ports: List ports allowed in a zone.

# Rich Rules:
    firewall-cmd --zone=<zone> --add-rich-rule='<rule>': Add a rich rule to a zone.
    firewall-cmd --zone=<zone> --list-rich-rules: List rich rules in a zone.
    firewall-cmd --zone=<zone> --remove-rich-rule='<rule>': Remove a rich rule from a zone.

# Reload and Management:
    firewall-cmd --reload: Reload the firewall configuration.
    firewall-cmd --panic-on: Enable panic mode (blocks all incoming/outgoing traffic).
    firewall-cmd --panic-off: Disable panic mode.
    firewall-cmd --query-panic: Check if panic mode is enabled.
    firewall-cmd --complete-reload: Reload and apply changes to all zones.
