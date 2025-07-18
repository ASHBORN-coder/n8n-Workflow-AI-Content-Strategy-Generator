# n8n-Workflow-AI-Content-Strategy-Generator
This repository contains an n8n workflow that automates market research and content ideation using AI. It gathers data from multiple sources, uses Google's Gemini AI to analyze the information, and generates strategic video topic ideas for a content calendar.
n8n Workflow: AI Content Strategy Generator
This repository contains an n8n workflow that automates market research and content ideation using AI. It gathers data from multiple sources, uses Google's Gemini AI to analyze the information, and generates strategic video topic ideas for a content calendar.

Table of Contents
Key Features

Workflow Diagram

How It Works

Project Structure

Prerequisites

Setup & Configuration

How to Use

Customization Ideas

Contributing


🚀 Key Features
🤖 AI-Powered Analysis: Leverages Google's Gemini AI to synthesize data and identify strategic content gaps.

📊 Multi-Source Data Aggregation: Fetches data from GNews, YouTube (popular and competitor videos), and Reddit to get a 360-degree view of the market.

💡 Automated Ideation: Automatically generates 5-7 relevant, low-competition video topic ideas in a single run.

📅 Content Calendar Integration: Directly populates a Google Sheet with new ideas, including titles, keywords, rationale, and status.

📢 Team Notifications: Instantly alerts the content team via Slack when new ideas are ready for review.

⚙️ Fully Automated: Designed to run on a schedule (e.g., weekly) to continuously supply fresh content ideas.

📊 Workflow Diagram
This diagram illustrates the flow of data from collection to final notification.

graph TD
    subgraph Data Collection
        A[Fetch GNews Articles] --> E;
        B[Fetch Popular YouTube Videos] --> E;
        C[Fetch Competitor Videos] --> E;
        D[Fetch Reddit Posts] --> E;
    end

    subgraph AI Processing
        E[Pre-process All Data] --> F[Analyze with Gemini AI];
        F --> G[Parse & Extract Topics];
        G --> H[Normalize Topic Data];
    end

    subgraph Output
        H --> I[Add Ideas to Google Sheet];
        I --> J[Run Once Trigger];
        J --> K[Notify Team on Slack];
    end

    subgraph End
        K --> L[End Workflow];
    end

⚙️ How It Works
Collect Data: The workflow fetches the latest articles, videos, and posts from GNews, YouTube, and a targeted Reddit community.

Pre-process: All the gathered data is combined and cleaned by a Code node into a single object for the AI.

Analyze with AI: The structured data is sent to the Gemini AI model with a prompt instructing it to act as a content strategist and find content gaps.

Parse & Normalize: The AI's JSON response is parsed, and the data for each topic is cleaned and standardized.

Log Ideas: Each topic suggestion is appended as a new row to a "Content Ideas" Google Sheet.

Notify Team: A final notification is sent to a Slack channel to let the team know that new ideas are available for review.

📁 Project Structure
/
├── content-strategy-workflow.json  # The n8n workflow file
├── README.md                       # This documentation file


📋 Prerequisites
An active n8n instance (cloud or self-hosted).

API keys and credentials for the following services:

GNews API

Google Cloud Platform with these APIs enabled:

Generative Language API (for Gemini)

YouTube Data API v3

Google Sheets API

Credentials configured in n8n for:

Google API (OAuth2)

Slack

🛠️ Setup & Configuration
Import Workflow: Copy the JSON from content-strategy-workflow.json and paste it onto your n8n canvas.

Configure Nodes: Update the following nodes with your API keys, IDs, and credentials.

Node Name

Parameter to Configure

Example Value

Fetch GNews Articles

URL (with your GNews API key)

...&token=YOUR_GNEWS_API_KEY

Fetch Popular YouTube Videos

URL (with your YouTube API key)

...&key=YOUR_YOUTUBE_API_KEY

Fetch Competitor Videos (Physics Wallah)

URL (with your YouTube API key and Channel ID)

...&channelId=...&key=...

Analyze with Gemini AI

Header Value for X-goog-api-key

YOUR_GEMINI_API_KEY

Add Ideas to Google Sheet

Credentials and Sheet ID

My Google Acc, 1a2b3c...

Notify Content Strategy Team (Slack)

Credentials and Channel

My Slack Acc, #content-strategy

Activate Workflow: Save your changes and activate the workflow.

🚀 How to Use
This workflow is designed to be run on a schedule (e.g., using a Cron node once a week) or triggered manually whenever you need a fresh batch of content ideas.

🧩 Customization Ideas
Add More Sources: Integrate with other platforms like Twitter, news APIs, or other subreddits.

Use Different Models: Swap out Gemini for another model like OpenAI's GPT-4.

Enhance the Prompt: Refine the prompt sent to the AI to ask for different formats, like blog post ideas or short-form video concepts.

Create a Dashboard: Use the data in the Google Sheet to power a Looker Studio or Grafana dashboard to track content performance.

🤝 Contributing
Contributions are welcome! Please feel free to fork the repository, make changes, and open a pull request.

Fork the repository.

Create a new branch (git checkout -b feature/your-feature-name).

Commit your changes (git commit -m 'Add some feature').

Push to the branch (git push origin feature/your-feature-name).

Open a Pull Request.

