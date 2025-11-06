# LinkedIn Content Automation with n8n & Notion

Automate your **entire LinkedIn content pipeline** — from idea to published post — using **n8n**, **Notion**, and **Google Gemini AI**.

## What's Inside

| Workflow | Purpose |
|--------|--------|
| [`LinkedIn_Post_generator.json`](LinkedIn_Post_generator.json) | Turns raw ideas into **polished, human-sounding LinkedIn posts** using AI |
| [`LinkedIn_Poster_with_image.json`](LinkedIn_Poster_with_image.json) | **Auto-posts** text + image content on the scheduled day |
| [`LinkedIn_Poster_text_only.json`](LinkedIn_Poster_text_only.json) | **Auto-posts** text-only content on the scheduled day |

---

## How It Works (Full Pipeline)

Idea → Notion → AI Draft → Review → Schedule → Auto-Post → Done

### 1. **Idea Capture & AI Drafting**
- Add a **Topic**, **Context**, and **Type** in Notion  
- Run `LinkedIn_Post_generator` workflow (You can schedule this to run automatically)  
- AI writes a **ready-to-post** LinkedIn update in your voice  
- Status changes: `New` → `In Review`

### 2. **Review & Schedule**
- Read the draft in Notion  
- (Optional) Add an image  
- Pick a **Schedule Date** and set status to `Scheduled`

### 3. **Auto-Publishing daily**
- `LinkedIn_Poster_with_image.json` or `LinkedIn_Poster_text_only.json` runs  
- Posts **only today’s scheduled content**  
- Updates Notion: `Scheduled` → `Posted` + timestamp

---

## Your Notion Database (Required)

## Setup

### 1. Notion Setup

1. Duplicate this Notion Database: https://animated-volleyball-052.notion.site/26c0ceff95eb8048ad32e4a8588f44e3?v=26c0ceff95eb81d4a2aa000c99d0292b

2. Create a Notion integration:
   - Go to [https://www.notion.so/my-integrations](https://www.notion.so/my-integrations)
   - Create a new integration
   - Save the API token
   - Share your database with the integration
  
### 2. LLM API key 
Let's use Gemini - it's free and easy to get an API key.
Go to https://aistudio.google.com and get your API key to be used in the workflow.
   
### 3. n8n Setup
Sign up to [n8n](https://n8n.partnerlinks.io/jzstea86fya1) (Cloud version works perfectly - free tier is fine)
1. **Import workflows into n8n**  
   → Go to n8n → Workflows → Import → Paste JSON

2. **Connect Notion**  
   → Add your Notion API key (Settings → Credentials)

3. **Connect LinkedIn**  
   → Use OAuth2 (follow prompts in n8n)

4. **Connect Google Gemini** *(for post generator)*  
   → Add your Gemini API key

5. **Activate the auto-posters**  
   → Turn on `LinkedIn_Poster_*` workflows

Done! Your content now runs on autopilot.

---

## Customize the AI Voice (Make It Sound Like You)

Edit the prompt in **"Message a model"** node in `LinkedIn_Post_generator` workflow to match your style/brand.
