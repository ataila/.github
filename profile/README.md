<p align="center"><img src="https://raw.githubusercontent.com/ataila/terraform-provider-ataila/main/docs/images/ataila-logo.png" alt="ATAILA" width="120"></p>

# ATAILA — developer tooling

This organisation publishes the tools that drive an **ATAILA Cloud Platform** installation from code. ATAILA is a sovereign cloud and Private AI platform for service providers and enterprises: the building blocks of the big clouds — compute, networking, S3-compatible storage, secrets, registry, monitoring — on infrastructure you control, plus your own GPU fleet, models and AI gateway.

## For developers

Every installation serves one versioned, documented API (`/api/v1`) next to its portal — customers, tenants, users, projects, releases, licence, brand and Private AI — with API tokens scoped to exactly the permissions you hold. There is no central endpoint: you talk to the installation you manage.

- **[terraform-provider-ataila](https://github.com/ataila/terraform-provider-ataila)** — registry address `ataila/ataila`. Manages an installation through that API; OpenTofu and Terraform are both first-class from 1.6, each tested against its oldest and newest supported release. [Terraform Registry](https://registry.terraform.io/providers/ataila/ataila) · [OpenTofu Registry](https://search.opentofu.org/provider/ataila/ataila) (listing in progress).
- **MCP for AI agents** — every installation also serves a Model Context Protocol endpoint: one tool per read operation, the same token, scopes and rate limit. Read-only by construction: no write operation is ever a tool.
- **Signed releases** — every release is signed with the ATAILA Kft. key (RSA-4096, fingerprint `9997D23D 22220320 3B02B5EE 51740425 A2D915F8`); [public key](https://github.com/ataila/terraform-provider-ataila/blob/main/docs/signing-key.asc).
- **Documentation** — [www.ataila.com/developers](https://www.ataila.com/developers): tokens, the API reference, the [provider](https://www.ataila.com/developers/terraform), [MCP](https://www.ataila.com/developers/mcp), the [changelog](https://www.ataila.com/developers/changelog). Within v1 the API only grows; a removal needs twelve months' notice. The provider follows semantic versioning.

## Install the provider

```hcl
terraform {
  required_providers {
    ataila = {
      source  = "ataila/ataila"
      version = "~> 1.0"
    }
  }
}
```

```shell
tofu init        # OpenTofu
terraform init   # Terraform
```

Set `ATAILA_ENDPOINT` to your portal's base URL and `ATAILA_TOKEN` to a token minted in the portal. Air-gapped installations use the mirror bundle attached to every [release](https://github.com/ataila/terraform-provider-ataila/releases).

## Editions

**ATAILA Cloud** — managed, multi-tenant. **ATAILA Enterprise** — licensed and self-hosted on your hardware, operated by us. **ATAILA Service Provider** — the multi-tenant platform in your datacentre, under your brand, for your customers; designed to run air-gapped. More at [www.ataila.com](https://www.ataila.com).

## Source, support and licensing

- The platform itself is not open source. The provider is [MPL-2.0](https://github.com/ataila/terraform-provider-ataila/blob/main/LICENSE).
- `terraform-provider-ataila` is a one-way, read-only mirror, built, tested and signed on ATAILA's own CI; nothing builds here.
- Issues are off. Questions and problems: **support@ataila.com** — for a failed API call, quote its `request_id`.
