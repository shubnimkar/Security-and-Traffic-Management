# Basic Commands:
    firewall-cmd --state: This command allows you to check the current status of Firewalld, whether it is running or not.
    
    firewall-cmd --get-default-zone: Retrieves the default zone that is applied when no specific zone is specified in other commands.
    
    firewall-cmd --get-active-zones: Lists the active zones, showing which zones are currently active.
    
    firewall-cmd --get-zones: Displays a list of all available zones in Firewalld.
    
# Zone Management:
    firewall-cmd --get-default-zone: Shows the default zone that Firewalld uses when no specific zone is specified.
    
    firewall-cmd --set-default-zone=<zone>: Sets the default zone to the specified zone.
    
    firewall-cmd --get-zone=<zone>: Provides information about the specified zone, including its configuration.
    
    firewall-cmd --list-all-zones: Lists all the available zones in Firewalld along with their configurations.
    
    firewall-cmd --zone=<zone> --add-interface=<interface>: Associates the specified interface with the specified zone.
    
    firewall-cmd --zone=<zone> --change-interface=<interface>: Changes the interface associated with the specified zone.
    
    firewall-cmd --zone=<zone> --remove-interface=<interface>: Removes the association of the specified interface from the specified zone.

# Service Management:
    firewall-cmd --get-services: Lists all available services that can be used in Firewalld.
    
    firewall-cmd --zone=<zone> --add-service=<service>: Adds the specified service to the specified zone, allowing traffic on the ports defined by the service.
    
    firewall-cmd --zone=<zone> --remove-service=<service>: Removes the specified service from the specified zone, blocking traffic on the ports defined by the service.
    
    firewall-cmd --zone=<zone> --list-services: Lists the services that are allowed in the specified zone.

# Port Management:
    firewall-cmd --zone=<zone> --add-port=<port>/<protocol>: Opens the specified port with the specified protocol in the specified zone.
    
    firewall-cmd --zone=<zone> --remove-port=<port>/<protocol>: Closes the specified port with the specified protocol in the specified zone.
    
    firewall-cmd --zone=<zone> --list-ports: Lists the ports that are allowed in the specified zone.

# Rich Rules:
    firewall-cmd --zone=<zone> --add-rich-rule='<rule>': Adds a custom rich rule to the specified zone, allowing you to define complex rules using advanced criteria.
    
    firewall-cmd --zone=<zone> --list-rich-rules: Lists the rich rules that are defined in the specified zone.
    
    firewall-cmd --zone=<zone> --remove-rich-rule='<rule>': Removes the specified rich rule from the specified zone.
# Reload and Management:
    firewall-cmd --reload: Reloads the firewall configuration, applying any changes that have been made.
    
    firewall-cmd --panic-on: Enables panic mode, which blocks all incoming and outgoing traffic.
    
    firewall-cmd --panic-off: Disables panic mode, allowing normal traffic flow.
    
    firewall-cmd --query-panic: Checks if panic mode is enabled or disabled.
    
    firewall-cmd --complete-reload: Performs a complete reload of Firewalld, reloading and applying changes to all zones.
