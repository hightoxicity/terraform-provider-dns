---
page_title: "Provider: DNS"
description: |-
  The DNS provider supports DNS updates (RFC 2136). Additionally, the provider can be configured with secret key based transaction authentication (RFC 2845) or can use GSS-TSIG (RFC 3645).
---


<!-- Please do not edit this file, it is generated. -->
# DNS Provider

The DNS provider supports resources that perform DNS updates ([RFC 2136](https://datatracker.ietf.org/doc/html/rfc2136)) and data sources for reading DNS information. The provider can be configured with secret key based transaction authentication ([RFC 2845](https://datatracker.ietf.org/doc/html/rfc2845)) or GSS-TSIG ([RFC 3645](https://datatracker.ietf.org/doc/html/rfc3645)).

Use the navigation to the left to read about the available resources and data sources.

## Example Usage

Using secret key based transaction authentication (RFC 2845):

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { ARecordSet } from "./.gen/providers/dns/a-record-set";
import { DnsProvider } from "./.gen/providers/dns/provider";
interface MyConfig {
  addresses: any;
  zone: any;
}
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string, config: MyConfig) {
    super(scope, name);
    new DnsProvider(this, "dns", {
      update: [
        {
          keyAlgorithm: "hmac-md5",
          keyName: "example.com.",
          keySecret: "3VwZXJzZWNyZXQ=",
          server: "192.168.0.1",
        },
      ],
    });
    new ARecordSet(this, "www", {
      addresses: config.addresses,
      zone: config.zone,
    });
  }
}

```

Using GSS-TSIG (RFC 3645):

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { ARecordSet } from "./.gen/providers/dns/a-record-set";
import { DnsProvider } from "./.gen/providers/dns/provider";
interface MyConfig {
  addresses: any;
  zone: any;
}
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string, config: MyConfig) {
    super(scope, name);
    new DnsProvider(this, "dns", {
      update: [
        {
          gssapi: [
            {
              keytab: "/path/to/keytab",
              realm: "EXAMPLE.COM",
              username: "user",
            },
          ],
          server: "ns.example.com",
        },
      ],
    });
    new ARecordSet(this, "www", {
      addresses: config.addresses,
      zone: config.zone,
    });
  }
}

```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `update` (Block List) When the provider is used for DNS updates, this block is required. Only one `update` block may be in the configuration. (see [below for nested schema](#nestedblock--update))

<a id="nestedblock--update"></a>
### Nested Schema for `update`

Optional:

- `gssapi` (Block List) A `gssapi` block. Only one `gssapi` block may be in the configuration. Conflicts with use of `key_name`, `key_algorithm` and `key_secret`. (see [below for nested schema](#nestedblock--update--gssapi))
- `keyAlgorithm` (String) Required if `key_name` is set. When using TSIG authentication, the algorithm to use for HMAC. Valid values are `hmac-md5`, `hmac-sha1`, `hmac-sha256` or `hmac-sha512`. Value can also be sourced from the DNS_UPDATE_KEYALGORITHM environment variable.
- `keyName` (String) The name of the TSIG key used to sign the DNS update messages. Value can also be sourced from the DNS_UPDATE_KEYNAME environment variable.
- `keySecret` (String) Required if `key_name` is set
A Base64-encoded string containing the shared secret to be used for TSIG. Value can also be sourced from the DNS_UPDATE_KEYSECRET environment variable.
- `port` (Number) The target UDP port on the server where updates are sent to. Defaults to `53`. Value can also be sourced from the DNS_UPDATE_PORT environment variable.
- `retries` (Number) How many times to retry on connection timeout. Defaults to `3`. Value can also be sourced from the DNS_UPDATE_RETRIES environment variable.
- `server` (String) The hostname or IP address of the DNS server to send updates to. Value can also be sourced from the DNS_UPDATE_SERVER environment variable.
- `timeout` (String) Timeout for DNS queries. Valid values are durations expressed as `500ms`, etc. or a plain number which is treated as whole seconds. Value can also be sourced from the DNS_UPDATE_TIMEOUT environment variable.
- `transport` (String) Transport to use for DNS queries. Valid values are `udp`, `udp4`, `udp6`, `tcp`, `tcp4`, or `tcp6`. Any UDP transport will retry automatically with the equivalent TCP transport in the event of a truncated response. Defaults to `udp`. Value can also be sourced from the DNS_UPDATE_TRANSPORT environment variable.

<a id="nestedblock--update--gssapi"></a>
### Nested Schema for `updateGssapi`

Optional:

- `keytab` (String) This or `password` is required if `username` is set, not supported on Windows. The path to a keytab file containing a key for `username`. Value can also be sourced from the DNS_UPDATE_KEYTAB environment variable.
- `password` (String, Sensitive) This or `keytab` is required if `username` is set. The matching password for `username`. Value can also be sourced from the DNS_UPDATE_PASSWORD environment variable.
- `realm` (String) The Kerberos realm or Active Directory domain. Value can also be sourced from the DNS_UPDATE_REALM environment variable.
- `username` (String) The name of the user to authenticate as. If not set the current user session will be used. Value can also be sourced from the DNS_UPDATE_USERNAME environment variable.

<!-- cache-key: cdktf-0.19.0 input-e9d4e9807f8ef1b1caf1a5ca0e0557f8226dc5a8c0c28ed2ac43d324ea610807 -->