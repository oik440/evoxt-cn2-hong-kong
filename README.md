# Evoxt CN2 Hong Kong: Is It Real CN2, Which Plan Do You Need, and What Does a Year Actually Cost? (All 11 Plans Compared)

Evoxt's Hong Kong node starts at **$2.99/month**, and **VM-1 at $5.99/month** is where most people should begin. The detail that decides whether it fits your workload: Evoxt describes Hong Kong as "CN2 optimized" routing and does not claim CN2 GIA. That one distinction sets the price, the peak-hour behavior, and who should buy something else.

Below you'll find all 11 Hong Kong plans with prices, what CN2 GT and CN2 GIA differ in, the traffic penalty for choosing Hong Kong over a standard region, a first-year cost estimate, and the workloads where this box is the wrong purchase.

## Quick pick

> **Most readers:** VM-1, $5.99/mo. One vCore, 2 GB RAM, 20 GB storage, 500 GB transfer. Enough for a site, a proxy endpoint, or a small API service.
> **Personal VPN or a test box:** VM-0.5, $2.99/mo. 512 MB is tight, but a single tunnel runs fine on it.
> **Several sites or a small store:** VM-2 at $11.99 or VM-3 at $14.99, where you get 4 GB RAM and a second or fourth core.

👉 [Check current Hong Kong CN2 plan pricing](https://bit.ly/EvoXt)

## All Hong Kong plans

Hong Kong belongs to Evoxt's Premium Network group, alongside Osaka. Every plan on this list ships with a 1 Gbps port, weekly automatic offsite backups, an IPv6 address, KVM isolation, a Layer 3 firewall you manage from the panel without SSH, browser VNC, full API access, rescue mode, and a 99.99% uptime target. Provisioning takes about 2.5 minutes, and you can move up a plan from the control panel without reinstalling the OS.

| Plan | CPU · RAM · Storage | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- |
| VM-0.5 | 1 core · 512 MB · 5 GB | 250 GB | $2.99/mo | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 core · 1 GB · 10 GB | 250 GB | $4.99/mo | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 core · 2 GB · 20 GB | 500 GB | $5.99/mo | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 cores · 2 GB · 20 GB | 500 GB | $6.95/mo | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 cores · 4 GB · 30 GB | 1,000 GB | $11.99/mo | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 cores · 4 GB · 30 GB | 1,000 GB | $14.99/mo | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 cores · 8 GB · 60 GB | 2,000 GB | $23.99/mo | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 cores · 8 GB · 60 GB | 2,000 GB | $29.99/mo | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 cores · 16 GB · 80 GB | 3,000 GB | $47.99/mo | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 cores · 16 GB · 80 GB | 3,000 GB | $60.95/mo | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 cores · 32 GB · 100 GB | 5,000 GB | $95.99/mo | [Deploy VM-16](https://bit.ly/EvoXt) |

All prices are monthly. Evoxt bills from monthly up to a three-year prepay, and longer cycles carry automatic discounts; the checkout page shows the exact figure for the term you select. The CPU on every plan is rated up to 6.0 GHz turbo, which is the company's main selling point and the reason single-threaded work runs well here.

## CN2 GT, CN2 GIA, and "CN2 optimized" are three different things

Evoxt's own description of the Hong Kong location reads: "Optimized routing to China via the high-quality CN2 network, offering fast, reliable connectivity for global customers and low-latency access to Asia due to Hong Kong's strategic location." That is the entire claim. No GIA anywhere in it.

The three tiers people mix up:

- **163 backbone** is China Telecom's default commercial internet. Cheap, congested at peak, and what most budget Asian VPS actually use.
- **CN2 GT (Global Transit)** is the mid tier. Better than 163, but it shares capacity with ordinary traffic. Off-peak it looks fine; during Beijing evening hours it degrades noticeably. Most listings advertising "CN2" at low prices mean GT.
- **CN2 GIA (Global Internet Access)** is dedicated, fully premium transit with near-zero packet loss and stable latency at peak. It costs providers enough per Mbps that real GIA plans start at many times Evoxt's prices.

The practical gap between GT and GIA appears almost entirely between **20:00 and 23:00 Beijing time**. Outside that window you can struggle to tell them apart. Inside it, GT starts dropping packets while GIA holds.

Where does Evoxt land? Its Hong Kong routing is positioned as CN2-optimized rather than pure GIA, which in practice should beat generic Hong Kong BGP and beat 163 backbone routing without promising GIA-grade stability at peak. If you need a contractual GIA guarantee for revenue-critical traffic, this is not that product.

One more thing worth knowing before you assume "CN2 optimized" means all three Chinese carriers. A third-party measurement page for the HKG.PRE.VM-1 configuration, checked today, reports median latency of roughly **78–112 ms on China Telecom** (Guangdong 78 ms, Beijing 112 ms) but **259–354 ms on China Unicom** and **228–289 ms on China Mobile**, with those paths running over 4837 and CMI rather than CN2. Single-source data from one monitoring page, so treat it as a direction rather than gospel, but it lines up with how these routes normally behave: the CN2 optimization does its work on the Telecom path, while Unicom and Mobile get routed the long way round. If your audience is mostly on Unicom or Mobile, test before you commit, and look at Osaka Premium as well, since it uses SoftBank return routing that tends to serve Telecom and Mobile better.

Either way, run your own latency and packet-loss checks against your real user locations during Beijing evening hours in the first week. That test costs you nothing but time.

👉 [Start with a VM-1 to test Hong Kong routing yourself](https://bit.ly/EvoXt)

## The same money buys half the transfer in Hong Kong

This is the trade-off that catches people after they've picked a plan. Hong Kong and Osaka Premium plans cost exactly what the Standard-region plans cost, but the monthly transfer allowance is roughly halved:

| Plan | Standard regions | Hong Kong / Osaka Premium |
| --- | --- | --- |
| VM-1 | 1,000 GB | 500 GB |
| VM-2 | 2,000 GB | 1,000 GB |
| VM-8 | 6,000 GB | 3,000 GB |
| VM-16 | 10 TB | 5 TB |

The reason is straightforward: CN2-optimized bandwidth costs more to deliver, so the plans bundle less of it instead of raising the sticker price.

Whether that hurts depends on your workload. Serving large media files, running a download mirror, or proxying video for a group of people will burn through 500 GB quickly. Web hosting, an API backend, a VPN endpoint for yourself, a game server, or a bot will not come close. A typical small site with a few thousand monthly visitors uses a small fraction of VM-1's allowance. Check your current egress before choosing; if you're moving more than roughly 15 GB a day, price out a Standard-region plan and accept the worse China routing, or step up a tier here.

## What a year actually costs

Evoxt's pricing is transparent in the narrow sense that the number on the plan page is the number you pay: no bandwidth overage fees, no CPU burst charges. Here's the list-price arithmetic for the two plans most people compare, before any coupon:

- **VM-1 at $5.99/mo:** $71.88 over twelve months. At the 10% annual prepay discount, about **$64.69/year**. Paid semi-annually in two lots, roughly $68.29 after the 5% discount.
- **VM-0.5 at $2.99/mo:** $35.88 over twelve months, about **$32.29/year** with the annual discount.

These figures are calculated from the published monthly rates and the standard cycle discounts; they are not a quote, and any coupon you enter at checkout will change them. Evoxt's deploy page has a coupon field near the top and tells you immediately whether a code applies to the plan and billing cycle you picked, so test whatever you have there rather than trusting a code list from a forum.

My own rule for any provider I haven't used: pay monthly for the first cycle, run the peak-hour tests, then switch to annual once you know the route holds. The savings from jumping straight to a year are real but small compared with the cost of prepaying for a node that turns out to be wrong for your users.

Refund terms vary by plan and are shown at checkout. Read them on the order page for the specific plan you're buying instead of relying on a number from a review site.

## Which plan fits which job

- **Personal VPN or proxy endpoint:** VM-0.5 ($2.99) is enough for one user. VM-0.75 ($4.99) if you want headroom for a second device or a small always-on service.
- **One site, a blog, or a lightweight app:** VM-1 ($5.99). 2 GB RAM runs a LEMP stack comfortably, and the 6.0 GHz single-core rating matters more here than core count.
- **Several sites or a small cross-border store:** VM-2 ($11.99) for 4 GB RAM across two cores, or VM-3 ($14.99) when you want four cores for concurrent PHP workers.
- **Game server, production database, or a Docker host running multiple containers:** VM-4 ($23.99) and up. 8 GB RAM is the point where you stop worrying about memory pressure.
- **Agency hosting dozens of client sites, or video transcoding:** VM-8 through VM-16. Above roughly $48/month, compare against Evoxt's dedicated server line before ordering, keeping in mind those are Malaysia-only.

Windows Server 2012, 2016, and 2022 are available in English and Chinese builds, so a Windows-only tool is not a blocker, though 512 MB and 1 GB plans are impractical for it.

## How it compares to the usual names

| Option | Positioning | Rough entry price |
| --- | --- | --- |
| Evoxt Hong Kong Premium | CN2-optimized, high clock speed, budget pricing | $2.99–$95.99/mo |
| BandwagonHost | Long-established genuine CN2 GIA, Hong Kong included | ~$89.99/mo for Hong Kong CN2 GIA entry |
| DMIT | High-end CN2 GIA, US West focus with Hong Kong presence | Reflects premium positioning |
| Tencent Cloud / UCloud | Hong Kong CN2 GIA, Chinese interface, RMB billing, domestic support | Varies; tighter compliance and content rules, renewal prices can rise |
| Sub-$5 Hong Kong VPS from budget hosts | Generic BGP or 163 backbone | Under $5, generally no CN2 |

The honest framing: Evoxt sits between generic Hong Kong BGP and true GIA, and you pay a fraction of GIA money for it. If a peak-hour dip translates directly into lost revenue, BandwagonHost or a domestic cloud's GIA tier is the safer purchase and the price difference reflects that. If you're hosting a site, a store, or a game server for China-based users on a budget, and you're willing to verify the route yourself in week one, the value case is strong.

## Where it falls short

Ticket-based support can be inconsistent on complex problems; Telegram gets faster answers. Occasional billing hiccups get resolved but do happen. Dedicated servers are Malaysia-only, so there's no upgrade path to bare metal in Hong Kong. There's no Chinese-language first-line support. A minority of users report connectivity instability, and a widely-read complaint thread about connection failures exists, which is exactly why the first-week test matters before you prepay a year. Treat this as a strong value provider rather than a five-nines SLA vendor.

## FAQ

**Is the Hong Kong node CN2 GIA?**
No. Evoxt describes it as CN2-optimized routing and makes no GIA claim. Expect it to beat generic Hong Kong BGP and 163 routing, not to match dedicated GIA at peak.

**Is 500 GB of transfer enough on VM-1?**
For a site, an API, a VPN endpoint, or a game server, yes, usually with plenty to spare. For media serving or a download mirror, no. Check your current monthly egress before ordering.

**Can I install Windows?**
Yes. Windows Server 2012, 2016, and 2022 are offered in English and Chinese versions. Pick a plan with at least 2 GB RAM for it.

**Can I get a refund if the routing disappoints?**
Evoxt publishes a money-back window for first orders, but the terms differ by plan and source, so confirm the exact policy on the checkout page for the plan you're buying. Paying monthly for the first cycle is the cheaper way to hedge.

**Can I upgrade later without reinstalling?**
Yes. The control panel lets you scale the plan up in a few clicks, keeping the existing disk and configuration.

## The decision, in one pass

Buy VM-1 at $5.99 if you're serving a site, a store, or an app to mainland users and Telecom is the dominant carrier among them. Drop to VM-0.5 for a personal tunnel. Go to VM-2 or VM-3 the moment you need 4 GB of RAM or a second core. Skip Evoxt entirely if your traffic is dominated by Unicom or Mobile users, or if any peak-hour degradation is unacceptable, and budget for GIA elsewhere.

Two things to confirm before you pay: the refund terms shown on your specific plan's checkout page, and your own latency numbers during Beijing evening hours in the first week. Everything else on this page you can decide from the table.

👉 [Compare the Hong Kong plans and pick your configuration](https://bit.ly/EvoXt)
