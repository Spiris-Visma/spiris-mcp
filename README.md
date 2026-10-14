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
* **Quotes** – create and search quotes, and convert a quote to an order or directly to an invoice
* **Orders** – create, search and update orders, and convert an order to an invoice
* **Customer invoices** – create, send and search invoices, register payments, send reminders, and void
* **Invoice drafts** – draft an invoice for your review, search and update drafts, and convert an approved draft to a real invoice
* **Articles** – create, search and update products and services, including their accounting rules; view article groups

**Purchasing**

* **Suppliers** – find, create and update
* **Supplier invoices** – create and search
* **Supplier invoice drafts** – draft a supplier invoice for your review, search and update drafts, and convert an approved draft to a real supplier invoice

**Accounting**

* **Vouchers** – create and search journal entries, including by fiscal year
* **Voucher drafts** – draft a journal entry for your review, search and update drafts, and convert an approved draft to a booked voucher
* **Accounts** – browse, create and update the chart of accounts and account types; check balances at a given date
* **Financial reports** – balance sheet and income statement, with prior-year comparison
* **Bank transactions** – view matched and unmatched bank transactions
* **Company summary** – multi-year overview of the company's financial health

**Other**

* **Attachments** – list and link files to your documents
* **Projects** – create, search and update
* **Cost centers** – list cost centers
* **Company settings** – view your company settings

**A note on drafts:** creating an invoice or voucher directly posts it to your accounts immediately. The draft tools exist so the AI can prepare something for you to look at first – nothing is booked until you approve the conversion.

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
3. Complete the OAuth login to authorise access to your Spiris account, and choose the company you want to work in
4. Activate the connector in your chat or workspace

Below are specific instructions for the most common platforms. If your platform isn't listed, look for "MCP", "custom connectors" or "external tools" in its settings.

### Claude

Custom connectors are supported on Claude Free, Pro, Max, Team and Enterprise. On the Free plan you can add one custom connector.

#### On Free, Pro or Max

1. Go to **Customize → Connectors**, click **+ Add** and choose **Add custom connector**
2. Enter name `Spiris` and URL `https://mcp.spiris.se/mcp`, then click **Add**
3. Complete the Spiris login
4. In a conversation, click **+** at the bottom left, choose **Connectors** and switch on Spiris

#### On Team or Enterprise

1. An Owner adds the connector under **Organization settings → Connectors → Add → Custom → Web**, with name `Spiris` and URL `https://mcp.spiris.se/mcp`
2. Each member then goes to **Customize → Connectors**, finds Spiris and clicks **Connect**

#### Claude Code

```bash
claude mcp add --transport http --scope user spiris https://mcp.spiris.se/mcp
```

`--scope user` makes Spiris available in all your projects. Leave it out to add Spiris to the current project only. Then run `/mcp` inside Claude Code to complete the OAuth login in the browser.

### ChatGPT

Full MCP support, including actions that create or change data, is available on ChatGPT Business, Enterprise and Edu. On Plus and Pro, custom MCP connectors may be limited to read-only use – check what your plan supports.

1. **Business, Enterprise or Edu:** a workspace admin must first allow custom MCP connectors (developer mode) under **Workspace Settings → Permissions & Roles → Connected Data**
2. Go to **[chatgpt.com/plugins](https://chatgpt.com/plugins)**, click **+** and choose **Add custom MCP server**
3. Name: `Spiris` · Server URL: `https://mcp.spiris.se/mcp` · Authentication: `OAuth`
4. ChatGPT warns that the server hasn't been reviewed by OpenAI. Select **I understand and want to continue**, then **Create as a plugin**
5. Complete the Spiris login. In a conversation, type `@` in the prompt box and choose Spiris

ChatGPT asks you to confirm before it runs tools that create or change data.

### VS Code

MCP servers are supported in VS Code with GitHub Copilot.

1. Create or open `.vscode/mcp.json` in your workspace
2. Add Spiris as an HTTP server:

   ```json
   {
     "servers": {
       "spiris": {
         "type": "http",
         "url": "https://mcp.spiris.se/mcp"
       }
     }
   }
   ```

3. Save the file and complete the Spiris login when VS Code asks you to

***

## Login and re-authentication

When you connect, you log in with OAuth via Spiris. The AI never sees your password – it receives a time-limited access token tied to your user account. When it expires, you'll be prompted to log in again.

Each connection works in one company – the one you choose when you log in. To work in another company, disconnect Spiris in your AI tool, connect again and choose the other company.

***

## Data and privacy

When you ask an AI to look something up or take an action in Spiris, that data travels through the AI platform – not just Spiris. The AI needs to see the data in order to work with it, just as you would. What the platform does with that data afterwards is governed by your subscription with them.

### How it differs by plan

* **Consumer plans** (free and personal paid tiers): Your conversations – including any accounting data shared during them – may in some cases be used to improve the model, unless you've actively opted out. Rules vary between providers, so check your specific settings.
* **Business plans** (Team, Business, Enterprise and equivalent): Data is generally not used for training, data processing agreements (DPAs) are in place, and you have more control over data handling.

**Our recommendation:** If you're handling financial data on behalf of clients – for example as an accountant – or if your company policy requires data to stay within defined boundaries, use a business plan with your AI provider. Always verify the current terms directly with your AI provider, as policies can change.

On Spiris's side: Spiris MCP runs within the EU, and we process data as we do with the rest of our product, in accordance with our privacy policy. We do not store your AI conversations – we see API calls the same way we see all other API calls to our platform. Once data is part of a conversation, your AI provider's terms apply, including where they store it.

***

## You are responsible for your accounting

AI can make mistakes. It may post to the wrong account, create an incorrect invoice, or suggest an action you didn't intend. Always review what the AI does before confirming – especially actions that send, post or modify your accounts.

Responsibility for the accuracy of your accounts lies with you, as it always has.

***

## Pricing

**Price per month: Free** _(beta)_

Spiris MCP is free to use while we're in beta.

***

## Releases

Release notes are published as [GitHub Releases](https://github.com/Spiris-Visma/spiris-mcp/releases) on this repository. Subscribe via GitHub's "Watch → Releases" to be notified.

***

## Feedback

We're building this based on what we hear. Found something that doesn't work, or missing a tool that should exist? Reach out – it directly shapes what comes next.

The fastest way is directly from your AI: the MCP server has a built-in `submit_feedback` tool. Just tell the AI you want to send feedback to the Spiris development team, and it handles the rest – no forms, no copy-pasting.

While Spiris MCP is in beta we don't offer support through our normal support channels. We do, however, actively monitor everything that comes in through `submit_feedback` and use it to fix issues and prioritise improvements.

***
