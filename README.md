# dolphin anty proxy: How to Set One Up the Right Way, Pick a Provider That Doesn't Get You Flagged, and Get Bulk Profiles Running

If you opened Dolphin Anty for the first time and hit the proxy field, you probably ran into the same wall everyone does: the browser itself is easy, but the profile is only as good as the IP sitting behind it. A Dolphin Anty profile with no proxy, or with a shared datacenter IP that twenty other people are using, is basically a fingerprinting exercise with extra steps.

This piece covers what actually goes in that proxy field, how to add proxies one at a time and in bulk, which proxy type to pick for which job, and how to avoid the common mistakes that get profiles flagged. 9Proxy is the provider used for the concrete numbers and setup examples below, but the mechanics apply to any residential provider you end up choosing.

## What Dolphin Anty does with your proxy

Dolphin{anty} is an antidetect browser built for multi-accounting. Each profile gets its own fingerprint — canvas, WebGL, fonts, timezone, language, screen size, the usual list — and you attach a proxy to each profile so the IP and the fingerprint line up.

That last part is where people trip. Dolphin Anty doesn't magically fix a bad proxy. If your profile claims to be a Chrome user on a home connection in Frankfurt and the IP resolves to a datacenter block in Virginia, the mismatch is louder than any canvas tweak you can make.

The proxy field supports HTTP, HTTPS and SOCKS5. Most residential providers hand you SOCKS5 or HTTP endpoints, and either works fine inside Dolphin Anty. SOCKS5 is the more common recommendation because it passes traffic more transparently, but if your provider only issues HTTP endpoints, use those — the difference in detectability is far smaller than the difference between a clean residential IP and a reused datacenter one.

## How to add a proxy to a Dolphin Anty profile

**Single profile, manual entry:**

1. Open Dolphin Anty and go to **Browser Profiles**.
2. Hit **Create Profile** in the top right.
3. Scroll to the **Proxy** section and click **New proxy** (or **Add proxy**).
4. Pick the type — HTTP or SOCKS5.
5. Paste the connection data your provider gave you: host, port, username, password.
6. Run the connection check Dolphin Anty offers before saving. If it fails, the profile is unusable no matter how good the fingerprint is.
7. Save the profile, then open it and confirm the IP from inside the browser (a quick "what is my IP" check is enough) matches the region you intended.

If your provider gives you a single-line string instead of separate fields, Dolphin Anty accepts the common `host:port:username:password` and `username:password@host:port` formats. Get the order wrong and the check will fail — this is the single most common setup error.

**Bulk import:**

Once you're past ten profiles, typing credentials by hand stops being viable. Dolphin Anty supports bulk proxy import: paste a list of proxy strings, one per line, and the browser validates and assigns them. The workflow that holds up in practice:

- Buy a batch of residential IPs (or a rotating endpoint) from your provider.
- Export or copy the endpoint list in the format Dolphin Anty expects.
- Paste the whole list into the bulk import dialog.
- Let Dolphin Anty run validation across the list, then discard the failures instead of assigning them.
- Assign one sticky IP per profile — not one IP across several profiles.

That last rule matters more than anything else on this page. Two Dolphin Anty profiles sharing an IP are linked accounts in the eyes of whatever platform you're working with, regardless of how different their fingerprints look.

👉 [Grab a residential IP package before you start building profiles](https://bit.ly/9-Proxy)

## Sticky IPs vs rotating IPs inside Dolphin Anty

This is the decision that determines whether 9Proxy's IP-based or GB-based plans make more sense for you.

**Sticky IPs** keep the same address for the life of the session — usually 10 to 30 minutes, sometimes longer depending on the provider. Use them for account management: logging into a marketplace seller account, an ad account, a social profile. The account sees the same IP every time, which is what you want. Reference material on the subject is consistent about this: multi-account setups are expected to hold stable endpoints, and providers that let you pin IPs per profile are the ones people recommend for exactly that reason .

**Rotating IPs** change the address on every request or on a timer. Use them for scraping, price monitoring, SERP checks, ad verification — anything where you're reading data rather than maintaining a login. Rotating also gets you around rate limits, because each request looks like a different visitor.

Dolphin Anty handles both. The profile doesn't care whether the endpoint behind it rotates; it just forwards traffic. What changes is your workflow: rotating endpoints are usually cheaper per gigabyte, sticky IPs are sold per address.

## Why the proxy provider choice matters more than the browser settings

A lot of Dolphin Anty guides spend their length on fingerprint settings and then mention proxies in one paragraph. That's backwards. Fingerprint spoofing is a solved, automated problem — the browser handles it. IP reputation is not solved, and it's the thing that actually triggers blocks.

Three properties to check before you buy anything:

- **Residential vs datacenter.** Datacenter IPs are cheap and fast and instantly recognizable as datacenter ranges. If the platform you're working with screens for ASN type, they fail immediately. Residential IPs come from real consumer connections and don't carry that signal.
- **Pool size and geography.** A small pool means you'll be recycling addresses that other users have already burned. 9Proxy advertises 20M+ residential IPs across 90+ countries, which is mid-to-large for this market and enough to spread accounts across regions without obvious clustering .
- **Rotation control.** You need to be able to hold an IP for a set duration, not just take whatever comes next. If a provider can't do session control, it's a scraping tool, not a multi-accounting tool.

9Proxy covers all three reasonably well, and the pricing is unusually low for residential — which is the main reason it shows up in antidetect browser discussions alongside Dolphin Anty. The tradeoff is that it's a leaner product than the enterprise-tier providers: no giant feature list, and support is live chat rather than a dedicated account manager . For a solo operator or a small team, that's usually the right trade.

## 9Proxy plans: IP-based, GB-based, and bundles

9Proxy splits its residential offering three ways. Which one you want depends on how you count usage — by number of accounts, or by bandwidth consumed.

### IP-based plans (unlimited bandwidth)

These are the ones you want for Dolphin Anty account management. You buy a fixed number of IPs, use them as you like, and bandwidth isn't metered .

| Plan | What you get | Price per IP | Savings shown | Buy |
| --- | --- | --- | --- | --- |
| Residential 100 IPs | 100 residential IPs | $0.24/IP | — | [Get the 100 IP plan](https://bit.ly/9-Proxy) |
| Residential 500 IPs | 500 residential IPs | $0.144/IP | −$48 | [Get the 500 IP plan](https://bit.ly/9-Proxy) |
| Residential 1000 IPs + 500 IPs | 1,500 IPs total | $0.084/IP | −$54 | [Get the 1,000 + 500 IP plan](https://bit.ly/9-Proxy) |
| Higher-volume tiers | Scales up from here | down to ~$0.018/IP | — | [See current high-volume rates](https://bit.ly/9-Proxy) |

The per-IP rate drops fast between tiers — roughly a third of the entry price once you're past a thousand IPs. If you're running 20 profiles you don't need any of these. If you're running 200, the difference between the first and third row is real money.

### GB-based plans (rotating residential)

Better fit for scraping, monitoring, and anything that burns bandwidth rather than holding sessions.

| Plan | Price per GB | Savings shown | Buy |
| --- | --- | --- | --- |
| Residential 5 GB | $3.00/GB | — | [Get the 5 GB plan](https://bit.ly/9-Proxy) |
| Residential 50 GB + 5 GB | $1.68/GB | −$66 | [Get the 50 + 5 GB plan](https://bit.ly/9-Proxy) |
| Residential 100 GB | $1.50/GB | −$150 | [Get the 100 GB plan](https://bit.ly/9-Proxy) |
| Residential 200 GB | $1.00/GB | −$400 | [Get the 200 GB plan](https://bit.ly/9-Proxy) |

The entry price per gigabyte is steep — $3.00/GB for the 5 GB pack — and that's the honest part of the lineup. Small bandwidth packs are priced for testing, not for production. If you're planning to scrape at volume, do the math on your monthly traffic first, because 5 GB disappears in an afternoon of image-heavy crawling.

At the top end, the rate drops to $0.68/GB, which is where 9Proxy becomes genuinely competitive against the bigger names in residential proxies .

### Bundle plans

9Proxy also sells IP and GB together, starting at $25 . This is the pragmatic middle ground if your work is mixed — some profiles that need to stay logged in, some scraping jobs that just need throughput. Bundles mean you're not buying two separate plans to cover both.

👉 [Compare the IP, GB, and bundle options side by side](https://bit.ly/9-Proxy)

## Matching 9Proxy endpoints to Dolphin Anty profiles

Once you have an active plan, the dashboard gives you endpoints in a few formats. The practical mapping:

- **Format:** take the `host:port:username:password` (or `user:pass@host:port`) string and drop it straight into Dolphin Anty's proxy field, or into your bulk list.
- **Type:** pick SOCKS5 if it's offered, HTTP otherwise.
- **Country targeting:** 9Proxy lets you choose the region per endpoint. Match it to the profile's timezone and language settings — a German profile with a Brazilian IP is a fingerprint mismatch the browser can't paper over.
- **Sticky sessions:** request a session-stable endpoint for account profiles. Test it before assigning it, and don't assume the duration — confirm it holds long enough for your longest login task.
- **Rotation:** for scraping profiles, point the rotating endpoint at a throwaway profile rather than a logged-in one.

Payment on 9Proxy runs through crypto and local payment methods, which is worth knowing if your usual card doesn't go through .

## Common problems and how to fix them

**The proxy check fails on a working endpoint.**
Nine times out of ten it's the credential order. Try the other format — `host:port:user:pass` versus `user:pass@host:port`. If both fail, test the same credentials in a plain browser or a curl request to isolate whether it's Dolphin Anty or the endpoint.

**Profiles open but platforms still restrict them.**
Check the geography. A profile configured for one country and an IP in another gets flagged by basic consistency checks. Align country, timezone, and language, and use one IP per profile.

**Everything slows down badly.**
Residential routing is slower than datacenter by nature. If it's unusable, check whether you're running traffic-heavy content through a residential endpoint — video, large downloads, and image scraping all feel bad on residential. Route that traffic through GB-based rotating plans instead, or separate the heavy profile from the daily-driver ones.

**A batch of imported proxies fails validation.**
Don't assign them anyway. Dolphin Anty's validation check exists because a dead endpoint looks exactly like a working one until you open the profile. Drop the failures and re-request replacements.

## Who this setup actually suits

Be honest about which side of the line you're on.

If you're managing a handful of accounts — a couple of seller profiles, some ad accounts, a few social logins — the 100 IP plan at $0.24/IP is the sane starting point. You get unlimited bandwidth on sticky IPs, you're not paying for gigabytes you won't use, and the per-IP cost is a rounding error against the value of not getting banned.

If your work is data collection — scraping, price checks, ad verification — skip the IP plans and go GB-based. Buy enough bandwidth that you're not repurchasing every ten days; the 50 GB and 100 GB tiers are where the per-gigabyte price stops being painful.

If you're doing both, a bundle is cheaper than two plans and saves you the mental overhead of tracking which endpoint belongs to which job.

What you shouldn't do is run fifty Dolphin Anty profiles off one rotating endpoint and hope the fingerprinting carries it. It won't. The browser's job is to make each profile look different; the proxy's job is to make each profile *come from* somewhere different. Those are two separate problems, and only one of them is solved by a settings menu.

👉 [Start with a 9Proxy residential plan and set up your first Dolphin Anty profile](https://bit.ly/9-Proxy)

## Quick FAQ

**Does Dolphin Anty include proxies?**
No. You bring your own. The browser configures the connection; the provider supplies the IP.

**HTTP or SOCKS5 for Dolphin Anty?**
SOCKS5 where it's available, HTTP otherwise. Both work; the endpoint quality matters far more than the protocol choice.

**Can I use one proxy for multiple profiles?**
Technically yes, practically no. Shared IPs link profiles, which defeats the point of running an antidetect browser in the first place.

**Are IP-based or GB-based 9Proxy plans better for Dolphin Anty?**
IP-based for anything with a login. GB-based for anything that reads data at volume. The billing model should follow what you're actually doing with the profile.

**How many IPs do I need?**
One per active profile, plus a handful spare for replacements when an endpoint dies or gets flagged. Buy in batches rather than topping up one at a time — the per-IP price drops sharply at 500 and 1,000.
