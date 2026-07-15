<div align="center">

# ⚡ ChatNexGen AI

### Self-Hostable WhatsApp CRM & No-Code Automation Engine

Built for the official **WhatsApp Business (Cloud) API** — real-time shared inbox, visual Kanban pipelines, automated broadcasts, a no-code flow builder, and an autonomous AI Healthcare Assistant.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-16-black?logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript)](https://www.typescriptlang.org/)
[![Supabase](https://img.shields.io/badge/Backend-Supabase-3ECF8E?logo=supabase)](https://supabase.com/)
[![WhatsApp Cloud API](https://img.shields.io/badge/WhatsApp-Cloud%20API-25D366?logo=whatsapp)](https://developers.facebook.com/docs/whatsapp/cloud-api)

[Features](#-key-modules--features) • [Tech Stack](#️-technological-stack) • [Getting Started](#-quick-start-guide) • [Configuration](#️-environment-configuration) • [Project Structure](#-project-structure)

</div>

---

## 📖 Overview

**ChatNexGen AI** turns the official WhatsApp Business Cloud API into a full CRM. Support and sales teams collaborate from a single shared inbox, track deals through visual pipelines, run compliant broadcast campaigns, and automate conversations with a drag-and-drop flow builder — all backed by an AI assistant capable of autonomously booking healthcare appointments.

---

## 🚀 Key Modules & Features

### 📥 Real-Time Shared Inbox
- **Multi-agent collaboration** — one official WhatsApp number, one unified interface for the entire team.
- **Thread assignment** — route conversations to specific agents, track state, and leave internal notes to avoid overlap.
- **Rich media support** — text, images, documents, audio, and interactive buttons.

### 📊 Visual Kanban Pipelines
- **Drag-and-drop deals** linked directly to live WhatsApp conversations.
- **Value tracking** — define pipeline stages and monitor total pipeline value in real time.
- **Quick actions** — trigger status updates or template messages straight from the board.

### 📢 Targeted Broadcast Campaigns
- **Meta-approved templates**, scheduled or dispatched instantly to custom contact lists.
- **Dynamic variable substitution** for per-client personalization.
- **Analytics dashboard** — delivery rates, read rates, and quick-reply click-throughs.

### 🔌 No-Code Flow & Automation Builder
- **Visual node builder** for automations triggered by keywords, new contacts, or schedules.
- **Conditional logic** branching on tags, custom fields, or business hours.
- **Action nodes** — webhooks, tagging, template follow-ups, and wait steps.

### 🏥 Autonomous AI Healthcare Assistant
- **Dual AI engine** — Google Gemini 1.5/2.0 Flash as primary responder, with automatic failover to OpenAI GPT-4o-Mini (or OpenRouter) via a built-in circuit breaker.
- **Strict 4-step appointment booking flow:**
  1. Collects patient name, age, and reason for visit in a single step.
  2. Presents available specialists.
  3. Calculates real-time open slots from doctor schedules and clinic hours, filtering out breaks and existing bookings.
  4. Confirms and logs the appointment.
- **Google Sheets sync** via a secure webhook script for real-time appointment logging.
- **Safety guardrails** — never diagnoses or prescribes, strips HTML from responses, and hands off to a human agent instantly on emergency/escalation keywords.

---

## 🛠️ Technological Stack

| Layer | Technology |
|---|---|
| **Frontend** | Next.js 16 (App Router), React 19, TypeScript |
| **Styling** | Tailwind CSS v4, Framer Motion, Lucide Icons |
| **Backend & Database** | Supabase (Postgres, Auth, Realtime, Storage, Row-Level Security) |
| **Messaging Gateway** | Meta WhatsApp Cloud API |
| **AI** | Google Gemini 1.5/2.0 Flash, OpenAI GPT-4o-Mini (fallback) |

---

## ⚙️ Environment Configuration

Copy the example environment file to get started:

```bash
cp .env.local.example .env.local
```

### Required

| Key | Description |
|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL. |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anonymous API key. |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key (server-only — used for webhook verification and cron triggers). |
| `ENCRYPTION_KEY` | 64 hex characters (32 bytes) for encrypting stored WhatsApp API credentials. |
| `META_APP_SECRET` | Used to verify HMAC signatures of incoming WhatsApp webhook events. |

### Optional — AI Healthcare Assistant

| Key | Description |
|---|---|
| `GEMINI_API_KEY` | Google Gemini API key (required for AI auto-replies). |
| `OPENAI_API_KEY` | OpenAI/OpenRouter API key (fallback responder). |
| `GOOGLE_SHEETS_WEBHOOK_URL` | Apps Script web app URL for syncing booked appointments. |
| `AUTOMATION_CRON_SECRET` | Secret used to secure automation cron routes. |

> ⚠️ Never commit `.env.local` — service-role keys and encryption secrets must stay server-side only.

---

## 🚀 Quick Start Guide

### 1. Clone & Install

```bash
git clone https://github.com/Kishore2005-Tech/whatsapp-crm-automation.git
cd whatsapp-crm-automation
npm install
```

### 2. Configure the Database

Run the SQL migrations in `supabase/migrations` against your Supabase instance:
- Apply the base schema for pipelines, broadcasts, and the automation engine.
- Apply the AI Healthcare schema and RLS policies (`013_ai_healthcare.sql` → `019_add_reminders_4h_2h.sql`).

### 3. Run Locally

```bash
npm run dev
```

Open **http://localhost:3000** to view the dashboard.

---

## 📂 Project Structure

```
├── docs/                      # Google Sheets Apps Scripts & offline documentation
├── src/
│   ├── app/                   # Next.js pages and API routing
│   │   ├── (auth)/            # Login, registration, password resets
│   │   ├── (dashboard)/       # Inbox, Contacts, Pipelines, Flows, AI Healthcare
│   │   └── (marketing)/       # Landing and product marketing pages
│   ├── components/            # Shared UI components and layout widgets
│   ├── context/                # Global React context providers
│   ├── hooks/                  # Reusable React hooks
│   ├── lib/                    # WhatsApp API helpers, caching, utilities
│   ├── services/                # AI Healthcare processing services
│   └── types/                   # TypeScript type declarations
├── supabase/
│   └── migrations/             # SQL database migration files
```

---

## 🤝 Contributing

Contributions are welcome! Please see [`CONTRIBUTING.md`](./CONTRIBUTING.md) for guidelines before opening a pull request.

## 📄 License

Licensed under the [MIT License](./LICENSE) — free to customize, self-host, and white-label for your own business or clients.

---

<div align="center">

## 👤 Author
 Kishore P | Full Stack Developer | [GitHub](https://github.com/Kishore2005-Tech)

</div>
