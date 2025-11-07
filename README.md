# LinkedIn Workflow with Approval (n8n)

A shareable n8n workflow that:
- Aggregates articles (RSS + optional PhantomBuster),
- Proposes LinkedIn topics via OpenAI,
- Generates images via Google Imagen,
- Sends a preview email for **Approve / Reject**,
- On **Approve**, posts to LinkedIn via Make webhook (or your own endpoint),
- Loops through 3–4 topics per run.

## 🔒 What you must set up

Replace all placeholders in the JSON before running:
- `__OPENAI_API_KEY__`
- `__GOOGLE_PROJECT_ID__`
- `__GOOGLE_LOCATION__` (e.g., `us-central1`)
- `__GOOGLE_IMAGEN_MODEL__` (e.g., `imagegeneration@006` or current)
- `__CLOUDINARY_CLOUD_NAME__`
- `__CLOUDINARY_UPLOAD_PRESET__` (unsigned preset recommended)
- `__PHANTOMBUSTER_API_KEY__` (if you use the PB branch)
- `__PHANTOMBUSTER_URL__` (if a fixed endpoint is present)
- `__MAKE_WEBHOOK_URL__`
- `__YOUR_EMAIL__` (Gmail Send node “to” value)

> Note: n8n **does not** export OAuth credentials. You’ll still need to connect your Gmail & Google credentials inside n8n’s Credentials.

## 🧩 Nodes to customize (prompts)
- **Fetching LinkedIn Topics1 (HTTP/OpenAI)** – Adjust voice, scope, and “priority regulations” in the prompt.
- **Enhanced image prompt (Code)** – Uses topic tokens to build a **text‑free** prompt. You can edit theme rules or remove them.
- **Caption style selector (Code)** – Rotate tone/structure for LinkedIn captions.

## 📰 Feeds
All RSS feed lists were cleared. Add your own in the RSS nodes (field `urls`).

## 🪝 Make / Webhook
If you use Make, open your **Custom Webhook** module and click **Redetermine data structure** after you change fields.  
Expect body JSON like:
```json
{
  "topic": "…",
  "caption": "…",
  "image_url": "https://res.cloudinary.com/__CLOUDINARY_CLOUD_NAME__/image/upload/..."
}
```

## ⚖️ License

Copyright (c) 2025 **MMS Ventures**

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
