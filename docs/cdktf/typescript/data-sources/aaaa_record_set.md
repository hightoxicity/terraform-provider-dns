---

<!-- Please do not edit this file, it is generated. -->
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "dns_aaaa_record_set Data Source - terraform-provider-dns"
subcategory: ""
description: |-
  Use this data source to get DNS AAAA records of the host.
---

# dns_aaaa_record_set (Data Source)

Use this data source to get DNS AAAA records of the host.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformOutput, Fn, Token, TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { DataDnsAaaaRecordSet } from "./.gen/providers/dns/data-dns-aaaa-record-set";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    const google = new DataDnsAaaaRecordSet(this, "google", {
      host: "google.com",
    });
    new TerraformOutput(this, "google_addrs", {
      value: Fn.join(",", Token.asList(google.addrs)),
    });
  }
}

```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `host` (String) Host to look up.

### Read-Only

- `addrs` (List of String) A list of IP addresses. IP addresses are always sorted to avoid constant changing plans.
- `id` (String) Always set to the host.

<!-- cache-key: cdktf-0.19.0 input-7db469a81767808aa5736fa2e189a7fb2686463358a86c8b28dc9ebdfbadcf5f -->