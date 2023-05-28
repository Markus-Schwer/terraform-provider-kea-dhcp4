---
page_title: "Provider: kea-dhcp4"
description: |-
  Provider for ISC Kea DHCP server for provisioning static DHCP leases.
---

# KEA-DHCP4 Provider

The provider uses Kea Control Agent's REST API for communication with an underlying Kea DHCP4 server (DHCP6 currently not supported), with optional reverse proxying for adding TLS and authentication.

Before using the provider, you must correctly specify the connection URL, credentials (if any), and path to DHCP server conffile on host (required for config-write API command).


## Requirements

* ISC Kea DHCP server v1.8+
* Terraform 0.14+

## Example Usage
```terraform
terraform {
    required_providers {
        kea-dhcp4 = {
            source = "Feliksas/kea-dhcp4"
            version = "1.1.0"
        }
    }
}

provider "kea-dhcp4" {
    kea_server_address    = "http://localhost:8080"
    kea_server_username   = "test"
    kea_server_password   = "1234"
    kea_server_configfile = "/etc/kea/kea-dhcp4.conf"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `kea_server_address` (String) IP or FQDN of host which serves Kea Control Agent API
- `kea_server_configfile` (String) Path to Kea DHCP4 server config (on server, required for config-write command)

### Optional

- `kea_server_password` (String) HTTP basic auth password (if configured)
- `kea_server_username` (String) HTTP basic auth username (if configured)