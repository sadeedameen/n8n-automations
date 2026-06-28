# Automated LinkedIn Post Generator (n8n)

This n8n workflow fully automates the creation and publishing of daily LinkedIn posts. It uses a two-step AI process to first brainstorm a trending topic, and then write a professional post tailored for corporate administration, posting it automatically at 10 AM every day.

## 🚀 Features
* **Fully Automated Scheduling:** Triggers automatically every day at 10:00 AM.
* **Two-Step AI Generation:** 
  1. Uses `gemini-3-pro-preview` to generate a highly relevant, trending AI topic.
  2. Uses `gemini-2.5-flash` to write a formatted, engaging LinkedIn post based on that topic.
* **Direct Publishing:** Automatically posts the generated content directly to your LinkedIn profile without any manual intervention.

## 🛠️ Workflow Steps
1. **Daily 10 am (Schedule Trigger):** Starts the workflow daily at 10:00 AM.
2. **Message a model (Gemini 3 Pro):** Given a system prompt to act as a trending topic expert, it generates a specific topic related to AI in Corporate Administration.
3. **Generate a content (Gemini 2.5 Flash):** Takes the generated topic and writes a complete, professional LinkedIn post following strict formatting rules (strong hook, no asterisks, no emojis, relevant hashtags).
4. **Create a post (LinkedIn):** Takes the final text and publishes it directly to LinkedIn.

## ⚙️ Prerequisites & Setup
To use this workflow, you need:
* n8n installed (Self-hosted or n8n Cloud).
* **Google AI Studio API Key:** For both Gemini 3 Pro and Gemini 2.5 Flash models.
* **LinkedIn OAuth2 Credentials:** Set up via n8n to allow posting to your profile.

## 🔧 Installation & Configuration
1. **Import the Workflow:** Download the JSON file and import it into your n8n instance.
2. **Set up Credentials:**
   * Configure Google PaLM API credentials for *both* AI nodes.
   * Configure LinkedIn OAuth2 API credentials for the posting node.
3. **Update your LinkedIn Profile ID:** In the "Create a post" node, you **must** change the `person` field to your own specific LinkedIn profile ID (URN ID). 
4. **Activate the Workflow:** Toggle the workflow to "Active".
