# Hostbase for Grok Bot

Hostbase is a property management system for hotels, serviced apartments and short-term rental operators. This plugin
connects Grok Bot (and Cursor) to your live Hostbase data, so you can ask about your business in plain language.

It contains one remote MCP server, `https://mcp.hostbase.ai/mcp`. It is the same server that backs the Hostbase
connectors for Claude and ChatGPT. Nothing runs on your computer.

## Connect

1. In Grok Bot, open **Connect apps**, find **Hostbase** and choose **Connect**.
2. A browser opens on Hostbase's sign-in page. Sign in with your Hostbase email and password.
3. You are connected to your own Hostbase organization automatically. You can't choose another one.

Your organization's admin must first turn the connector on in Hostbase under **Settings → AI Connectors**. You can
revoke a connection there at any time.

## What it can do

Grok Bot connects **read-only**. It can:

- look up reservations, arrivals, departures and in-house guests (`list_reservations`, `get_reservation`)
- check which rooms are free and which dates are blocked (`check_availability`, `list_blocked_dates`, `list_room_types`)
- quote a stay from the Hostbase pricing engine, with the direct and per-channel price (`get_rate_quote`)
- report occupancy, ADR, RevPAR, Gross Booking, VAT & taxes, Gross Revenue, Net Revenue and net payout for any period,
  by channel, room type, month and more, plus how the landlord's share is defined (`get_performance`)
- read guest reviews, refunds and the cash settlement ledger (`list_guest_reviews`, `list_refunds`,
  `list_cash_settlements`)
- describe your account, properties and access (`get_account`)

Booking changes (create, change, move, cancel, block rooms) are available to Claude and ChatGPT, where every change
needs an approval card that you click. Grok Bot's Auto-review can approve a connected app's action without asking you,
and Bots run unattended routines, so Hostbase doesn't give Grok Bot write access.

Not available through any connector: guest messaging, issuing refunds, pricing changes and user management.

## Privacy and access

- The connection runs with your own Hostbase role and permissions, and is locked to your organization.
- Sign-in uses OAuth 2.1 with PKCE. Your password goes only to Hostbase, never to Grok Bot or Cursor.
- Connections last up to 180 days. They end at once if you change your password, leave the organization, lose a
  qualifying role, or your admin turns the connector off.

Privacy policy: https://hostbase.ai/privacy · Terms: https://hostbase.ai/terms · Support: founders@hostbase.ai
