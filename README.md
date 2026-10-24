# scraperapi vs scrapingbee: Real Pricing Math, Credit Costs, and How to Pick the Right One for Your Targets

Both tools solve the same problem — you send a request to an API endpoint, they handle proxy rotation, CAPTCHAs, retries, and optional headless browser rendering, then hand you back HTML or JSON. Neither gives you raw proxy lists, and neither is a "proxy provider" in the Bright Data or Oxylabs sense. The real difference between them shows up in the billing math: **ScrapingBee charges by feature, ScraperAPI charges by feature *and* by domain**. Which one costs you less depends almost entirely on what you're scraping — and most comparison posts online never run those numbers properly. This article does.

> **Quick take:** If your targets are heavy on Amazon, Google, or Walmart and you want pre-parsed JSON back, ScraperAPI's domain surcharges buy you parsing work you'd otherwise build yourself — and its higher-tier plans work out cheaper per successful request at volume. If your target list is broad, changes weekly, or is JS-heavy, ScrapingBee's flat feature-based pricing is easier to predict. Either way, both offer free credits with no credit card: ScraperAPI gives you a 7-day trial with **5,000 API credits**, ScrapingBee gives 1,000. Most readers comparing these two end up starting with ScraperAPI's Hobby plan at $49/mo (or the free trial first) — 👉 [start with 5,000 free API credits and test it on your own target list](https://www.scraperapi.com/pricing?fp_ref=coupons).

## ScraperAPI's full plan lineup

Here's every plan currently shown on ScraperAPI's pricing page, monthly and annual billing both included:

| Plan | Monthly price | Annual (per month) | API credits | Concurrent threads | Link |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [View Hobby plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [View Startup plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [View Business plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling (most popular) | $475 | $427.50 | 5,000,000 | 200 | [View Scaling plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [View Professional plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [View Advanced plan](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | [Contact sales for a custom quote](https://www.scraperapi.com/pricing?fp_ref=coupons) |

Annual billing saves 10% on every tier. On the Scaling plan that's $475 → $427.50 per month, or **$570 saved over a year** — worth knowing before you click monthly out of habit.

Every plan, including Hobby, ships with the same core feature set: JS rendering, premium residential and mobile IPs, automatic CAPTCHA and anti-bot handling, IP rotation, custom headers and sessions, JSON auto-parsing, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Higher tiers add things like DataPipeline, full crawler access, and pay-as-you-go overflow.

A couple of limits only show up in the plan details, and they matter more than most reviews admit:

- **Geotargeting on Hobby and Startup is US & EU only.** Country-level geotargeting starts at Business. If you need to scrape from, say, Japan or Brazil on the cheap plan, you'll be disappointed.
- **The analytics dashboard on Hobby and Startup only keeps the last 30 days of data.** Business and above keep it unlimited. Fine for debugging last week's failures, annoying for month-over-month trend analysis.

## ScrapingBee's plans, for comparison

ScrapingBee's current pricing page lists five tiers, all monthly, all excluding VAT:

| Plan | Monthly price | API credits | Concurrent requests |
| --- | --- | --- | --- |
| Hobby | $19 | 75,000 | 25 |
| Freelance | $49 | 250,000 | 50 |
| Startup | $99 | 1,000,000 | 100 |
| Business | $249 | 3,000,000 | 200 |
| Business + | $599 | 8,000,000 | 400 |

The page promises "Cancel anytime, no questions asked!" and offers 1,000 free API credits to try before paying — there's no ongoing free plan, just the one-time signup credits.

## The billing difference nobody explains clearly

This is where most comparisons get lazy, and where your actual bill gets decided.

**ScrapingBee multiplies credits by feature.** A plain request costs 1 credit. Turn on JavaScript rendering and it jumps to 5. Route through the premium proxy and it goes to 10. Premium proxy *plus* JS rendering is 25 credits. The stealth proxy pool with JS hits 75 credits per request for the hardest targets. Which site you're hitting doesn't matter — only what the site forces you to enable. With 250,000 credits on the $49 Freelance plan, that's 250,000 plain pages, but only about 50,000 JS-rendered ones, or roughly 3,300 stealth requests.

**ScraperAPI multiplies by feature and by domain.** A standard page is 1 credit. Then the domain surcharges kick in: Amazon costs 5 credits per request, Google and Bing (including subdomains) cost 25, LinkedIn costs 30. Sites behind Cloudflare, Datadome, or PerimeterX add 10 credits per request when ScraperAPI successfully bypasses the protection. JS rendering and premium proxies stack their own multipliers on top — one third-party benchmark roundup estimates JS rendering lands around 10 credits on ScraperAPI versus 5 on ScrapingBee.

So two jobs of identical page count can produce wildly different bills depending on the target list. A 100,000-credit Hobby plan is 100,000 generic pages, 20,000 Amazon pages, or 4,000 Google SERP pages.

The flip side: those surcharges buy you dedicated endpoints that return **pre-parsed structured JSON**. Amazon at 5 credits and Google SERP at 25 credits come back as fields you can feed straight into your pipeline, instead of raw HTML you'd have to parse, maintain, and repair every time a page layout changes. If you'd otherwise spend developer days building and babysitting an Amazon parser, 5 credits per request is a reasonable price.

Two safeguards make this pricing model manageable, and they're buried in ScraperAPI's FAQ where most articles never look:

1. **The Domain Cost Estimator** in your dashboard shows the exact credit cost of any URL before you scrape it — no guessing.
2. **The `max_cost` parameter** lets you cap any single request, so one accidental hit on a 30-credit domain can't blow through your balance.

## Head-to-head at matched price points

At $49/month — the entry point for both — you get ScraperAPI's Hobby plan with 100,000 credits, or ScrapingBee's Freelance plan with 250,000. On pure credit volume, ScrapingBee wins 2.5x. But if half your pages need JS rendering, ScrapingBee's effective count drops to 50,000 while ScraperAPI's generic-page equivalent stays higher, and the gap flips again once Google or Amazon enters your target list.

At the 1M-credit tier, ScrapingBee's Startup plan is $99/month against ScraperAPI's $149/month Startup. That's the tier where ScrapingBee's price advantage is most visible. Above that, the comparison gets murkier: ScrapingBee tops out at Business+ ($599/mo, 8M credits), while ScraperAPI runs Scaling ($475/mo, 5M credits), Professional ($975/mo, 10.5M credits), Advanced ($1,975/mo, 21.5M credits), and custom Enterprise tiers — more headroom for genuinely high-volume operations.

One third-party comparison run in 2026 put it this way: ScraperAPI "tends to win on raw price per successful request at high volume and gives you more granular control over proxy type per request," while ScrapingBee's headless Chrome rendering is "more mature out of the box" for teams that don't want to think about proxy types at all. For simple non-JS requests, back-calculated cost per successful request generally favors ScraperAPI; once JS rendering and premium proxies enter the mix, the gap narrows and can flip depending on your request mix.

If you want to run this math on your own numbers, the pricing page shows both billing cycles side by side — 👉 [open the pricing page and compare monthly vs annual rates](https://www.scraperapi.com/pricing?fp_ref=coupons).

## What happens when things go wrong

Failed requests cost nothing on both platforms — you're only billed for successes, which both services confirm on their own pages. That's a bigger deal than it sounds, because anti-bot failures can easily eat half your requests on protected targets.

Concurrency is handled differently from what you might expect. Exceed your ScraperAPI plan's thread limit and you get a 429 response telling you to slow down and retry. The official wording: "There's no extra charge for going over, the request is simply turned away rather than queued." So over-limit requests aren't billed, they're just rejected — you retry them yourself.

When credits run out mid-month, ScraperAPI pauses scraping by default until renewal. Hobby through Professional plans can opt into **auto-upgrade**, which automatically bumps you to the next plan at better per-credit rates when you hit the wall. Scaling and above get **pay-as-you-go** instead: keep scraping at a fixed per-credit rate up to a monthly spending cap you set yourself. Annual plans can also renew early for a fresh batch of credits. If your scrape volume is spiky, knowing this exists beats discovering it at 2 a.m. when your job silently stops.

## Features that only one side has

A few capabilities aren't mirrored, and they occasionally decide the choice on their own:

- **Screenshot API:** ScrapingBee only. If you need visual verification of what actually rendered, that's a genuine differentiator. ScraperAPI has no equivalent.
- **AI extraction:** ScrapingBee offers `ai_query` and `ai_extract_rules`, letting you pull fields from arbitrary pages using natural language. ScraperAPI's answer is structured endpoints plus LangChain and LlamaIndex integrations.
- **Official SDKs:** ScraperAPI covers Python, Node, PHP, Ruby, and Java. ScrapingBee ships official SDKs for Python and Node only — fine if you're in either ecosystem, a real friction point if you're not.
- **Scale tooling:** ScrapingBee leans on batch tooling; ScraperAPI offers an async scraper with high thread limits on upper tiers.
- Both now have an MCP server, both offer dedicated Amazon/Google extraction endpoints, and both were still shipping structured JSON for these domains as of September 2026.

On ownership: ScrapingBee was acquired by Oxylabs in 2025, which connects it to a very large residential proxy network. ScraperAPI remains independent and has owned Rainforest API since 2024. Neither fact changes the API surface much, but it's worth knowing who you're signing a year-long contract with.

## Which one is more reliable?

Independent benchmarks — including Scrapeway's monthly test runs — have generally shown **ScraperAPI with higher success rates but slower responses**, and ScrapingBee faster but less consistent on some protected targets. Success rates shift month to month as anti-bot systems evolve on both sides, so any single month's ranking is a snapshot, not a verdict. The sensible move either way is a pilot: throw your actual target list at both with the free credits before committing to an annual plan.

## Who should pick neither, or something else

Honest answer: if what you actually want is a pool of residential IPs to plug into your own scraper stack — raw proxies with usernames, passwords, and rotation logic you control — neither of these is the right tool. They're managed APIs that abstract all of that away. And if your targets are mostly easy, non-JS pages at low volume, even $19/month on ScrapingBee's Hobby plan (or ScraperAPI's free 1,000-credit plan) might be more than you need.

## FAQ

**Is ScraperAPI or ScrapingBee cheaper?**
Depends on your targets. At matched $49/month, ScrapingBee's Freelance gives 2.5x the credits. At the 1M tier, ScrapingBee is $99 vs ScraperAPI's $149. But per *successful useful request*, ScraperAPI often comes out ahead for high-volume, mostly-plain-HTTP jobs, and its structured endpoints replace parser maintenance on Amazon/Google/Walmart pipelines. Run the credit math on your own target list — both vendors change prices periodically.

**Do failed requests cost credits?**
No, on both platforms. Only successful requests are billed.

**Does ScraperAPI have a free trial?**
Yes — a 7-day trial with 5,000 API credits, no credit card required. There's also a standing free plan with 1,000 credits and up to 5 concurrent connections if you just need to test.

**Can I switch plans later?**
ScraperAPI lets you upgrade anytime from the billing page, and auto-upgrade (on Hobby through Professional) moves you up automatically when credits run out. ScrapingBee's pricing page states you can cancel anytime with no questions asked.

## Final pick, by situation

- **Scraping Amazon, Google, or Walmart at volume and want structured JSON back** → ScraperAPI's domain surcharges are effectively paying for your parser. Business at $299/month (3M credits, 100 threads, country-level geotargeting) is the tier where the economics fully click. 👉 [check current Business plan pricing](https://www.scraperapi.com/pricing?fp_ref=coupons)
- **Mostly plain-HTML targets, no JS, high volume, cost per request is your KPI** → ScraperAPI Hobby or Startup, annual billing, and let the 10% discount do its thing.
- **Broad or fast-changing target list, lots of JS-heavy pages, want screenshots or AI extraction** → ScrapingBee's feature-based pricing predicts costs more cleanly; its $99 Startup tier is the strongest price point in this matchup.
- **Just experimenting** → take both free tiers, no card needed on either side. ScraperAPI's 5,000 trial credits give you roughly four times the test volume of ScrapingBee's 1,000, which is enough to actually benchmark your hardest three targets instead of guessing.

One last thing before you click buy: check the exact credit cost of your top domains in the Domain Cost Estimator first. Two minutes there tells you more about which plan you need than any comparison article — this one included. 👉 [sign up for ScraperAPI and run your target list through the free trial](https://www.scraperapi.com/pricing?fp_ref=coupons)
