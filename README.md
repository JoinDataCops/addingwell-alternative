# DataCops vs Addingwell

A short, technical comparison between DataCops and Addingwell (now "Addingwell by Didomi" since the April 2025 acquisition). Useful if you are evaluating server-side tracking, consent management, CAPI mediation and bot filtering for a 2026 stack.

## TL;DR

Addingwell is a managed Server-side Google Tag Manager (sGTM) host. It sits in the same lane as Stape, TAGGRS and Tracklution. As of April 2025 it is owned by Didomi (EUR 72M acquisition, Marlin Equity Partners-backed) and is being folded into an enterprise platform alongside Sourcepoint (acquired July 2025) over a two-year unification roadmap. Entry pricing is EUR 90/mo (Pay-as-You-Go, 2M requests). Sandbox is free at 100k requests/month.

DataCops is a different category. It is first-party trust infrastructure that runs on a CNAME on the customer's subdomain, with no GTM container required. It bundles five products: first-party analytics (ad-blocker and ITP immune), server-side CAPI to Meta + Google + TikTok + LinkedIn, signup fraud detection, traffic-fraud validation and a TCF 2.2 certified consent manager. Setup is one `<script>` tag plus one CNAME record. Live in 5 to 30 minutes.

The two products solve overlapping but not identical problems.

## Architecture comparison

### Addingwell

- Managed Google Tag Manager Server container hosted on EU infrastructure
- Customer points a subdomain (typically `gtm.example.com`) at the Addingwell endpoint
- Tags configured inside Google Tag Manager UI
- 99.99% uptime SLA on the entry tier
- Native pairing with Didomi CMP since the acquisition
- Compliance: GDPR-aligned, EU-hosted; does NOT hold SOC 2, ISO 27001, HIPAA, DORA

### DataCops

- First-party CNAME on customer subdomain (`datacops.example.com`)
- Single `<script>` tag added to `<head>`
- No GTM container, no Cloud Run, no sGTM concepts to learn
- Bundles analytics + CAPI + bot filter + signup fraud + CMP into one runtime
- IP reputation database: 361,873,948,495+ IPs and network ranges tracked (live counter), including 146.4B+ datacenter ranges, 11.9B+ VPN endpoints, 620M+ proxy/anonymizer IPs
- Compliance: GDPR-compliant data processing (active), CCPA (active), Custom DPA on Enterprise (active), EU and US data residency (active), TCF 2.2 first-party consent (active), SOC 2 Type II (in progress), Google Consent Mode v2 (in progress), DSAR API (planned), SSO/SAML (planned), ISO 27001 (planned)

## Setup time

```
Addingwell:    DNS + GTM container + tag templates + Consent Mode v2 wiring
               Typical: 4 to 16 hours initial setup, plus ongoing tag work

DataCops:      DNS + 1 script tag
               Typical: 5 to 30 minutes initial setup, no ongoing GTM work
```

## Pricing comparison

```
Addingwell:
  Sandbox       Free       100k requests/mo
  Pay-as-You-Go EUR 90/mo  2M requests/mo
  (higher tiers quoted; Didomi CMP licensing separate, USD 2k-15k/yr typical)

DataCops:
  Basic         Free       2,000 sessions/mo, unlimited bot detection,
                           500 signup verifications, free CMP
  Growth        $7.99/mo   5,000 sessions, unlimited Meta + Google CAPI
  Business      $49/mo     50,000 sessions, HubSpot integration, full CRM sync
  Organization  $299/mo    300,000 sessions, full feature set
  Enterprise    Talk to Sales  Dedicated runtime, dedicated IP DB, custom DPA, residency
```

Worked agency example (5 client sites at ~4M requests/month each):

```
Addingwell:  ~EUR 900/mo for sGTM hosting alone
             +Didomi CMP licensing (USD 2k-15k/yr) for consent management
             Bot/fraud filtering and analytics dashboard NOT included

DataCops:    5 x $49/mo Business = $245/mo total
             Bundled: analytics + CAPI + bot filter + signup fraud + CMP
```

## When to pick which

Pick **Addingwell** if:
- You are already a Didomi CMP customer and want consent + sGTM under one vendor
- Your developer team has deep GTM template investment
- You are an enterprise buyer comfortable with the EUR 90+/mo entry tier

Pick **Stape** if:
- You need attested SOC 2, ISO 27001, HIPAA, DORA on the sGTM host
- You are technical and comfortable with sGTM concepts
- You need 80+ server-side tag templates (Klaviyo, Attentive, Snap, Reddit, etc.)

Pick **TAGGRS** or **Tracklution** if:
- Cost is the primary driver (entry around EUR 25 to 31)
- You want a non-technical, EU-hosted sGTM

Pick **DataCops** if:
- You want CAPI + consent + bot filtering + first-party analytics in one bill
- You don't want to run an sGTM container at all
- You're an SMB or small agency and the bundle math (one vendor, four problems solved) wins

## Limitations to know

DataCops:
- SOC 2 Type II is in progress, not attested
- ISO 27001 is planned, not attested
- SSO and SAML are planned, on the Enterprise tier roadmap
- DSAR API and downstream deletion (Meta, Google) are planned
- Younger product than Stape; agency case-study pile is still growing

Addingwell:
- No SOC 2, ISO 27001, HIPAA or DORA per Seresa.io's 2026 agency comparison
- Pricing has migrated upmarket post-Didomi acquisition (April 2025)
- Two-year unification roadmap with Didomi + Sourcepoint introduces roadmap risk for SMB customers
- No true multi-tenant agency dashboard (per the same agency comparison)

## References

- Didomi acquires Addingwell announcement: https://www.didomi.io/blog/didomi-addingwell-acquisition
- Didomi acquires Sourcepoint (AdExchanger): https://www.adexchanger.com/privacy/consent-management-consolidates-with-didomis-acquisition-of-sourcepoint/
- Stape compliance posture: https://stape.io/
- Seresa.io agency comparison (Stape vs Addingwell): https://seresa.io/blog/server-side-gtm/stape-vs-addingwell-which-managed-sgtm-host-is-right-for-agencies
- DataCops product: https://joindatacops.com/conversion-api

## License

This README is published under CC BY 4.0 by DataCops. Reuse and reference welcome with attribution.

---

Research by [DataCops](https://www.joindatacops.com) · First-party tracking, consent infrastructure & fraud prevention.
