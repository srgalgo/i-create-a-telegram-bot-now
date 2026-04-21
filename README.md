# SwapzyCryptoTrade Bot

This bot now supports the main Telegram workflow for `SwapzyCryptoTrade`:

- private bot menu for users
- KYC request flow with document upload
- admin KYC approval or rejection buttons
- VIP and orders group access links for approved users
- sell order creation for KYC-approved users
- buy button in the orders group
- managed trade flow with escrow confirmation, payment proof, and completion tracking
- warning, mute, anti-link, welcome, and goodbye moderation tools
- premium public onboarding in the General group
- public `/rules`, `/fees`, `/price`, and `/join` commands
- configurable support contact in the pinned onboarding message

## Important business note

This version manages the workflow, records, approvals, timers, and trade states inside Telegram.

It does **not** automatically send crypto on-chain from your wallet yet.

That final part needs a separate secure wallet integration because it involves private keys, custody, and real money movement. For now, the bot helps admins, buyers, and sellers complete the process and keeps the records.

## Setup

1. Install Node.js if needed.
2. In this folder, run `npm install`
3. Put your real bot token in `.env`
4. Start the bot with `npm start`
5. On Windows, you can also double-click `START-BOT.cmd`

## Telegram permissions you need

Promote the bot to admin in the groups where it works.

Give it permission to:

- delete messages
- ban users
- restrict users
- invite users
- manage join requests

Also disable privacy mode in BotFather:

1. Open BotFather
2. Open your bot
3. Go to `Bot Settings`
4. Go to `Group Privacy`
5. Turn it off

## Chats you should prepare

You said your business uses these areas:

- general group
- VIP group
- buy/sell orders group
- admin KYC approval group

Optional:

- trade desk admin group

If you do not set a separate trade desk group, the KYC admin group will also receive trade cases.

## Admin setup commands

Run these commands in the correct Telegram group:

- `/setgeneral`
- `/setvip`
- `/setorders`
- `/setkycadmin`
- `/settradedesk`

Run these as owner or admin:

- `/setwallet YOUR_ESCROW_WALLET_ADDRESS`
- `/setfees 1 1`
- `/settimeout 30`
- `/setsupport @username`
- `/setrules YOUR_RULES_TEXT`
- `/setpriceinfo YOUR_PUBLIC_PRICE_TEXT`
- `/businessstatus`
- `/postwelcome`

## User flow

Users should message the bot privately and press `/start`.

Private menu actions:

- `Request KYC`
- `Sell Order`
- `Payment Details`
- `Access Links`
- `My Status`
- `Help`

General group commands:

- `/join`
- `/rules`
- `/fees`
- `/price`

## KYC flow

1. User taps `Request KYC`
2. User sends:
   - full name
   - country
   - document type
   - KYC file or photo
3. Bot sends the request to the KYC admin group
4. Admin taps approve or reject
5. Approved users can request VIP and orders access links

## Trade flow

1. Seller saves payout details
2. Seller creates a sell order in private chat
3. Bot posts the order to the orders group
4. Buyer taps `Buy`
5. Buyer continues in private chat:
   - amount to buy
   - wallet address for receiving crypto
6. Bot creates a live trade case
7. Seller is asked to send escrow to the business wallet
8. Admin taps `Escrow Received`
9. Buyer gets seller payment details and uploads payment proof
10. Seller or admin marks the trade complete after release

## Main files

- [src/index.js](C:/Users/Admin/Documents/Codex/2026-04-21-i-create-a-telegram-bot-now/src/index.js)
- [src/store.js](C:/Users/Admin/Documents/Codex/2026-04-21-i-create-a-telegram-bot-now/src/store.js)
- [config/business-defaults.json](C:/Users/Admin/Documents/Codex/2026-04-21-i-create-a-telegram-bot-now/config/business-defaults.json)
- [config/default-settings.json](C:/Users/Admin/Documents/Codex/2026-04-21-i-create-a-telegram-bot-now/config/default-settings.json)

## Before 24/7 hosting

Test these first:

1. Private `/start`
2. KYC request and admin approval
3. Access link request
4. Sell order post
5. Buy flow
6. Escrow confirm
7. Payment proof upload
8. Trade complete

After that, move it to 24/7 hosting.
