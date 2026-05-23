# @maybexenos/baileys-wrapper

<div align="center">

**A clean and powerful Baileys wrapper for WhatsApp bots**

*Maintained by SIFAT*

---

![Version](https://img.shields.io/badge/version-1.0.0-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)
![Node](https://img.shields.io/badge/node-%3E%3D18-brightgreen?style=flat-square)
![Language](https://img.shields.io/badge/language-JavaScript-yellow?style=flat-square)

</div>

---

## What is this?

`baileys-wrapper` is a lightweight JavaScript library that wraps the [Baileys](https://github.com/MYB-SIFU/baileys-wrapper) WhatsApp Web API, making it easier and faster to build WhatsApp bots with a clean event-driven structure.

---

## Features

- **Easy client setup** — connect to WhatsApp with minimal configuration
- **Command handler** — load and manage bot commands from a folder automatically
- **Middleware support** — run custom logic before every command executes
- **QR & Pairing code** — supports both QR scan and phone number pairing
- **Database built-in** — simple persistent storage via `simpl.db`
- **Group caching** — automatic group metadata caching for faster responses
- **Cooldown system** — built-in rate limiting for commands
- **VCard builder** — easily create and send contact cards
- **Message collector** — await user replies within a conversation flow

---

## Installation

```bash
npm install @maybexenos/baileys-wrapper
```

---

## Quick Start

```js
const { Client, Events } = require("@maybexenos/baileys-wrapper");

const bot = new Client({
    auth: {
        adapter: "multi",
        dir: "./state"
    },
    messaging: {
        prefix: "!"
    },
    owner: ["1234567890"]
});

bot.command("ping", async (ctx) => {
    await ctx.reply("Pong!");
});

bot.ev.on(Events.ClientReady, () => {
    console.log("Bot is ready!");
});

bot.launch();
```

---

## Available Exports

| Export | Description |
|---|---|
| `Client` | Main WhatsApp bot client |
| `CommandHandler` | Auto-loads commands from a directory |
| `Config` | JSON-based config loader |
| `Cooldown` | Rate limiting helper |
| `VCardBuilder` | Build and send contact cards |
| `Events` | Event name constants |
| `MessageType` | Message type constants |
| `Formatter` | Text formatting helpers (bold, italic, etc.) |
| `Baileys` | Raw Baileys instance (for advanced use) |
| `Consolefy` | Styled console logger |
| `Gktw` | Utility helpers (bug analyzer, did-you-mean) |

---

## Client Options

```js
new Client({
    auth: {
        adapter: "multi",         // "multi" or "single"
        dir: "./state",           // auth directory
        usePairingCode: false,    // use pairing code instead of QR
        phoneNumber: "1234567890" // required if usePairingCode is true
    },
    connection: {
        suppressBaileys: true,    // suppress Baileys logs
        alwaysOnline: false,      // stay online always
        selfReply: false          // respond to own messages
    },
    messaging: {
        prefix: "!",              // command prefix
        autoRead: false           // auto-read messages
    },
    database: {
        dir: "./database"         // database folder
    },
    owner: ["1234567890"]         // owner phone numbers
});
```

---

## Text Formatting

```js
const { Formatter } = require("@maybexenos/baileys-wrapper");

Formatter.bold("Hello")         // *Hello*
Formatter.italic("Hello")       // _Hello_
Formatter.strikethrough("Hello") // ~Hello~
Formatter.monospace("Hello")    // ```Hello```
Formatter.quote("Hello")        // > Hello
```

---

## License

This project is licensed under the [MIT License](LICENSE).

Copyright (c) 2026 **SIFAT**
