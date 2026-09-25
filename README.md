<div align="center">

<img src="assets/cover.png" alt="AppsFlyer through HeyMetra's MCP server" width="100%">

# AppsFlyer &times; HeyMetra

**Installs, cost and revenue by media source and campaign.**

Your subscription revenue lives in AppsFlyer. What you paid to get those subscribers does not. Ask about both in the same sentence.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-appsflyer-1f6feb)](https://heymetra.com/connectors/appsflyer/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> Which media sources drove the most installs last month?

> What did each campaign cost per install last month?

> Which campaigns returned more revenue than they cost?

> How did installs and cost move day by day this month?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect AppsFlyer

**1. Open the Security centre in AppsFlyer**

Sign in to AppsFlyer, open the account menu at the top right and choose Security centre, then Manage your AppsFlyer API tokens. You need an account admin to see this screen.

> It is an account-level screen, not a per-app one. One token covers every app in the account; which app HeyMetra reads is decided by the app ID in the next step, not by the token.

**2. Create a token of type API**

The screen offers more than one kind. Choose API. Copy the value in full: it runs past seven hundred characters, so select all of it rather than what fits in the box.

> AppsFlyer revoked every token issued before 10 March 2026. An older one that has been sitting in a password manager will fail, and the failure looks like a permission problem rather than an expiry.

**3. Find the app ID**

On Android it is the package name, exactly as the Play Store shows it, such as com.example.app. On iOS it is the letters id followed by the App Store number, such as id123456789.

> One connection is one app. AppsFlyer publishes no way to ask a token which apps it may report on, so a second app is a second connection.

**4. Paste both in HeyMetra and save**

Choose AppsFlyer on the Connections screen, paste the token and the app ID, and save. HeyMetra checks the pair against AppsFlyer immediately, by asking for one finished day, so a token that cannot actually report fails here rather than later in a conversation.

**5. Name your reporting currency**

Optional, and worth doing. AppsFlyer publishes no currency anywhere in its reports, so without this every amount comes back with no currency stated rather than with the wrong one assumed.

**6. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Cursor or Codex. HeyMetra gives you the address and the key to paste, and AppsFlyer answers there.

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans only an owner can add it, under Organization settings._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — Settings → Security and login → Developer mode, then chatgpt.com/plugins</summary>

Paste the address above into Settings → Security and login → Developer mode, then chatgpt.com/plugins.

_The address has to end in /mcp here._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_XAI calls this “bring your own MCP”._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Settings → Connectors → Custom connector → Remote</summary>

Paste the address above into Settings → Connectors → Custom connector → Remote.

_Perplexity documents it as a Pro, Max and Enterprise feature._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_Or a .mcp.json in the project root; /mcp inside a session shows what connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Under an [mcp_servers.<name>] section, then codex mcp login._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Leave the static OAuth fields empty; HeyMetra does not need them._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_The key is serverUrl, not url, unlike every other JSON client._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Full account access** | Lets your assistant read anything in this account to answer your questions. The figures are the provider's own, not ones HeyMetra has checked. It can also propose changes: none is applied until you approve it, and HeyMetra cannot undo one afterwards — 31 days a report. A longer question is refused rather than answered with a fortnight's figures.; AppsFlyer allows 120 reports a day for the account and 24 per app, and that allowance is SHARED with the export page in the AppsFlyer dashboard. Reports pulled here are reports you cannot download there that day.; Re-engagement and acquisition count different people. A re-engagement figure is not part of an install figure, and the same person can appear in both.; A cohort follows the people who ARRIVED in a period forwards, so it never adds up to that period's own installs or revenue.; Apple's SKAdNetwork figures for iOS are a second count of the same campaigns, not a part of the first: they cover every device rather than only those that allowed tracking, and adding the two counts an install twice.; A SKAdNetwork postback arrives at least a day after the install and version 4 sends two more later still, so the last few days are always still filling in.; Cost is whatever the media source chose to report, and most report nothing. An absent cost is unknown, not zero, so ROI and cost-per-install are withheld rather than computed from a gap.; AppsFlyer does not state a currency anywhere in its reports. Unless one was entered when connecting, the amounts are in the app account's own currency and nothing here can say which.; Revenue is GROSS: what the buyer paid, before the store's cut and tax. The rates AppsFlyer deducts can be read, but no net figure is computed from them, because that needs the country of each purchase and the reports do not carry one.; The rows carry the people. AppsFlyer's raw columns include device identifiers, the advertising id, the IP address and the device model of an app's users.; Ninety days. AppsFlyer deletes raw data past that and no request reaches it; the aggregate reports go further back.; Twenty-four pulls a day per report type, and that allowance is SHARED with the export page in the AppsFlyer dashboard. Raw data read here is raw data you cannot download there that day.; Real time, so the same question asked twice can return different rows.. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask anything about this account and get the answer from its live data. Reads only, and the figures are the provider's own rather than ones HeyMetra has checked.
- Propose a change to this account. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve, inside bounds that live in code rather than in a prompt: ±50% on a budget, 5 campaigns per action and 20 changes a rolling day, and an approval that expires after 30 minutes. [How that works](https://heymetra.com/security/).

## When something goes wrong

<details>
<summary>Saving fails and says the token was rejected, on a token you have used before.</summary>

**Why:** Tokens issued before 10 March 2026 19:00 UTC were revoked by AppsFlyer, and a revoked token is refused the same way a wrong one is.

**Fix:** Generate a new token of type API in the Security centre.

</details>

<details>
<summary>Saving fails although AppsFlyer clearly knows the app: the app ID is right and the token is new.</summary>

**Why:** Reporting through the Pull API is part of the AppsFlyer plan rather than a setting on the token. An account without it can list its apps and cannot read a single daily figure.

**Fix:** Ask your AppsFlyer account manager whether Pull API reporting is on your plan. No token change will substitute for it.

</details>

<details>
<summary>Saving fails saying that app ID is not in the account.</summary>

**Why:** The iOS form is the letters id followed by the App Store number, and a bare number or a bundle identifier is a different string.

**Fix:** Use com.example.app on Android and id123456789 on iOS. The app's own page in AppsFlyer shows the exact value.

</details>

<details>
<summary>An export you started in the AppsFlyer dashboard is refused for the rest of the day.</summary>

**Why:** The report allowance is shared. AppsFlyer permits 120 reports a day per account and 24 per app, counted across the API and the dashboard's own export page together.

**Fix:** The allowance resets at 00:00 UTC. HeyMetra reuses a recent answer where it can, so exploring through your assistant uses less of it than the same questions asked by hand. It is still one allowance, not two.

</details>

<details>
<summary>The iOS numbers do not match what the ad network reports.</summary>

**Why:** On iOS, AppsFlyer counts devices that allowed tracking and Apple's SKAdNetwork reports every device with the detail removed. They are two counts of the same campaigns and neither contains the other.

**Fix:** Ask for the SKAdNetwork figures alongside, and read them as a second measurement. Adding the two counts every install that appears in both twice.

</details>

## What HeyMetra reads from AppsFlyer

One connection is one app. Ask your assistant about installs, cost, revenue, clicks and impressions for a period, grouped by day, media source, campaign, channel, country or app, up to 31 days at a time. Figures AppsFlyer marks as not reported are labelled as such instead of being summed into a total that looks complete. When you connect, you choose whether your assistant may also propose changes: creating an imported audience, adding people to one or removing them, and a request to erase one user's data. Every change it proposes waits for your approval.

<details>
<summary>About AppsFlyer</summary>

AppsFlyer is the mobile attribution and marketing analytics platform that ties installs, in-app events, and revenue back to the media that drove them. It’s the source of truth for mobile ROI and channel performance.
</details>

## One connection, not seven

The reason to read AppsFlyer through HeyMetra rather than through a server that only knows AppsFlyer is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://heymetra.com/connectors/google-ads/) · [Meta](https://heymetra.com/connectors/meta-ads/)

**Analytics** — [Google Analytics 4](https://heymetra.com/connectors/google-analytics-4/) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Shopify](https://heymetra.com/connectors/shopify/) · [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://heymetra.com/connectors/stripe/) · [HubSpot](https://heymetra.com/connectors/hubspot/) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — **AppsFlyer** · [RevenueCat](https://heymetra.com/connectors/revenuecat/) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Google Calendar](https://heymetra.com/connectors/google-calendar/) · [Google Meet](https://heymetra.com/connectors/google-meet/) · [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [AppsFlyer connector page](https://heymetra.com/connectors/appsflyer/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with AppsFlyer. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
