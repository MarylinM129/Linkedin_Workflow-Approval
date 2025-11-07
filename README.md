# LinkedIn Workflow with Approval  
### Built by MMS Ventures — Licensed under Apache 2.0  

---

## 🧩 Overview  

This open-source automation is a full **LinkedIn company-page posting system** built in **n8n**.  
It gathers content from multiple data sources, generates AI-driven post ideas, creates visuals, sends posts for approval by email, and automatically publishes approved content via Make (Integromat).  

---

## ⚙️ Features  

- Aggregate ~600+ articles from RSS feeds and optional LinkedIn scraping (via PhantomBuster)  
- Generate topical LinkedIn post ideas with **OpenAI**  
- Create brand-consistent, text-free images using **Google Imagen**  
- Approve or reject content directly in **Gmail**  
- Automatically publish approved content to your **LinkedIn company page** through **Make Webhook**  
- Modular design — edit or extend any step to fit your stack  

---

## 🧠 Customize your brand prompts  

This workflow includes **three key AI nodes** you can personalize to match your brand, industry, and tone.  
You’ll find them in the JSON as follows:

1. **Fetch LinkedIn Topics** *(HTTP Request Node)*  
   - Generates the raw post ideas and key talking points.  
   - Edit the system + user prompts in the body JSON.  
   - Adjust topic focus, industry keywords, and tone of insight (e.g., replace “EU regulation” with “sustainability,” “SaaS,” “AI ethics,” etc.).  

2. **Caption Style Selector** *(Code Node)*  
   - Controls the writing style of captions.  
   - Choose from or design new tone presets (e.g. professional, friendly, bold, reflective).  
   - Add your own heuristics for voice or brand personality.  

3. **Enhanced Image Prompt** *(Code Node)*  
   - Defines how Google Imagen builds visuals.  
   - Replace or expand the default thematic buckets, palettes, and composition logic.  
   - Example: swap “EU map cartography” for “wellness minimalism,” “fintech data visuals,” or “product mockups.”  

These are your creative control points — everything else (data ingestion, approvals, posting) is fully automated.  

---

## 🪄 Structure  

1. **RSS Feeds + PhantomBuster Inputs** → Aggregate content  
2. **Format for GPT-1** → Normalize + filter recency  
3. **Fetch LinkedIn Topics (HTTP Request)** → Generate topic ideas  
4. **Enhanced Image Prompt (Code)** → Build image prompt for Google Imagen  
5. **Generate Image** → Create image asset  
6. **Email Approval Loop (Gmail)** → Approve / reject content  
7. **Make Webhook** → Post approved items to LinkedIn  
8. **Loop Control** → Continue to next topic  

---

## 🔐 Credentials to Replace  

In your local n8n instance, open the **Credentials** section and set up new credentials or environment variables for each of these integrations:  

| Integration | Placeholder in JSON | Description |
|--------------|--------------------|--------------|
| **OpenAI API Key** | `<YOUR_OPENAI_API_KEY>` | For topic + caption generation |
| **Google Imagen Credentials** | `<YOUR_GOOGLE_IMAGEN_KEY>` | For image generation |
| **PhantomBuster API Key / URLs** | `<YOUR_PHANTOMBUSTER_CLIENT_ID>` | For LinkedIn content scraping |
| **Cloudinary Credentials** | `<YOUR_CLOUDINARY_CLOUD_NAME>` + `<YOUR_CLOUDINARY_UPLOAD_PRESET>` | For image hosting |
| **Make Webhook URL** | `<YOUR_MAKE_WEBHOOK_URL>` | For LinkedIn posting |
| **Gmail Integration** | `<YOUR_GMAIL_CONNECTION>` | For approval emails |

Replace each placeholder with your own secure keys.  
Do **not** commit credentials publicly.  

---

## 🧱 Setup  

1. Import the `.json` workflow into your **n8n** instance.  
2. Replace all credential placeholders listed above.  
3. Review and edit prompts in the three customizable nodes.  
4. Connect your Make Webhook to handle posting to LinkedIn.  
5. Activate the workflow and watch it build, review, and post content automatically.  

---

## 🪶 License  

Licensed under the **Apache License 2.0**  
Copyright © 2025 MMS Ventures  

You may freely use, modify, and distribute this workflow under the terms of the Apache 2.0 License.  

---

## 💬 Contact  

If you adapt or build upon this workflow, please credit **MMS Ventures** and share improvements back with the community.  
Pull requests and forks are welcome.  
