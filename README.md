# Spiris MCP

Connect your AI tools to Spiris. Use Claude, ChatGPT or any other MCP-compatible AI platform directly with your accounting – create invoices, look things up, manage customers and more, without leaving the AI tool you already use.

In this first phase, Spiris MCP works against **Bookkeeping & Invoicing**. More areas will follow.

This repository hosts the public release notes. The server is hosted by Spiris — there is nothing to install or run.

> **Early access.** Spiris MCP is in beta. It works, but the feature set is limited and things will change as we learn. Expect rough edges, and don't be surprised if something doesn't behave as expected. If you run into issues or find something missing – we want to know.


***

## What is MCP?

MCP (Model Context Protocol) is an open standard that lets AI assistants connect directly to external tools and data sources. Think of it as a universal connector between AI and the software you already use.

MCP is developed by Anthropic and supported by a growing number of AI platforms and tools.

***

## What you can do

Once connected, you can use your AI to work with **Bookkeeping & Invoicing**. In this first phase the available tools are:

**Sales**

* **Customers** – find, create and update customers; view customer groups
* **Orders** – create, search and update orders, and convert an order to an invoice
* **Customer invoices** – create, send and search invoices, register payments, send reminders, and void
* **Articles** – create, search and update products and services, including their accounting rules; view article groups

**Purchasing**

* **Suppliers** – find, create and update
* **Supplier invoices** – create and search

**Accounting**

* **Vouchers** – create and search journal entries, including by fiscal year
* **Accounts** – browse, create and update the chart of accounts and account types; check balances at a given date
* **Company summary** – multi-year overview of the company's financial health

**Other**

* **Attachments** – list and link files to your documents
* **Projects** – create, search and update
* **Cost centers** – list cost centers
* **Company settings** – view your company settings

We're continuously improving existing tools and adding new ones based on what users need.

***

## Before you begin

To use Spiris MCP you need two things:

1. **A Spiris subscription** – you need to be a customer of ours.
2. **An AI platform that supports MCP** – your own account or subscription with an AI platform that has MCP connectors enabled (for example Claude or ChatGPT).

## Activate the service

Getting Spiris MCP ready takes three steps:

1. In **My Services**, under **[Manage subscriptions](https://vismaonline.com/subscriptions)**, add the **MCP – Beta** service. This makes it available to the company, but doesn't give anyone access yet.
2. Under **[Manage users](https://vismaonline.com/users)**, switch it on for each user who should be able to connect – including yourself.
3. On the **Home** page, open **MCP – Beta** and click **Accept terms and conditions**.

Steps 1 and 2 require the **Administrator** role.

***

## Getting started

Once the service is active, connect your AI tool using this URL: `https://mcp.spiris.se/mcp`

The general steps are the same regardless of which tool you use:

1. Find the MCP or custom connector settings in your AI tool
2. Add a new connector with the URL above
3. Complete the OAuth login to authorise access to your Spiris account
4. Activate the connector in your chat or workspace

Below are specific instructions for the most common platforms. If your platform isn't listed, look for "MCP", "custom connectors" or "external tools" in its settings.

### Claude

Remote MCP connectors are supported on Claude Free, Pro, Max, Team and Enterprise.

#### On Pro or Max

1. Go to **Settings → Connectors**
2. Click **+** and add name `Spiris` and URL `https://mcp.spiris.se/mcp`
3. Click **Add** and complete the Spiris login
4. Activate Spiris in a conversation via the **+** menu in the chat

#### On Team or Enterprise

An Owner must first add the connector under **Organization settings → Connectors → Add**. Users can then activate it for themselves.

#### Claude Code

```bash
claude mcp add --transport http spiris https://mcp.spiris.se/mcp
```

Then run `/mcp` inside Claude Code to complete the OAuth login in the browser.

### ChatGPT

Requires Developer Mode, available on Plus, Pro, Business and Enterprise.

1. Enable Developer Mode: **Workspace Settings → Permissions & Roles → Connected Data → Developer mode**
2. Go to **Settings → Apps & Connectors → Add new connector**
3. Name: `Spiris` · URL: `https://mcp.spiris.se/mcp` · Authentication: `OAuth`
4. Check _"I trust this application"_ and click **Create**
5. Complete OAuth login, then activate Spiris via the tools menu in the chat

### VS Code

MCP support in VS Code is available through extensions such as GitHub Copilot and Continue. The general steps are:

1. Open your MCP configuration file (typically `.vscode/mcp.json` or your extension's settings)
2. Add a new server entry with URL `https://mcp.spiris.se/mcp` and type `http`
3. Save and reload. Complete the OAuth login when prompted

***

## Login and re-authentication

When you connect, you log in with OAuth via Spiris. The AI never sees your password – it receives a time-limited access token tied to your user account. When it expires, you'll be prompted to log in again.

***

## Data and privacy

When you ask an AI to look something up or take an action in Spiris, that data travels through the AI platform – not just Spiris. The AI needs to see the data in order to work with it, just as you would. What the platform does with that data afterwards is governed by your subscription with them.

### How it differs by plan

* **Consumer plans** (free and personal paid tiers): Your conversations – including any accounting data shared during them – may in some cases be used to improve the model, unless you've actively opted out. Rules vary between providers, so check your specific settings.
* **Business plans** (Team, Business, Enterprise and equivalent): Data is generally not used for training, data processing agreements (DPAs) are in place, and you have more control over data handling.

**Our recommendation:** If you're handling financial data on behalf of clients – for example as an accountant – or if your company policy requires data to stay within defined boundaries, use a business plan with your AI provider. Always verify the current terms directly with your AI provider, as policies can change.

On Spiris's side: we process data as we do with the rest of our product, in accordance with our privacy policy. We do not store your AI conversations – we see API calls the same way we see all other API calls to our platform.

***

## You are responsible for your accounting

AI can make mistakes. It may post to the wrong account, create an incorrect invoice, or suggest an action you didn't intend. Always review what the AI does before confirming – especially actions that send, post or modify your accounts.

Responsibility for the accuracy of your accounts lies with you, as it always has.

***

## Pricing

**Price per month: Free** _(beta)_

Spiris MCP is free to use while we're in beta. We will introduce a monthly fee before the general release – we'll communicate this clearly and in advance, so you won't be surprised.

***

## Releases

Release notes are published as [GitHub Releases](https://github.com/Spiris-Visma/spiris-mcp/releases) on this repository. Subscribe via GitHub's "Watch → Releases" to be notified.

***

## Feedback

We're building this based on what we hear. Found something that doesn't work, or missing a tool that should exist? Reach out – it directly shapes what comes next.

The fastest way is directly from your AI: the MCP server has a built-in `submit_feedback` tool. Just tell the AI you want to send feedback to the Spiris development team, and it handles the rest – no forms, no copy-pasting.

While Spiris MCP is in beta we don't offer support through our normal support channels. We do, however, actively monitor everything that comes in through `submit_feedback` and use it to fix issues and prioritise improvements.

***
