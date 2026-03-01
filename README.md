# 🌦️ Agentic Weather AI (Amazon Bedrock + Claude 4.5 Sonnet)

An autonomous weather intelligence agent powered by **Amazon Bedrock** and **Claude 4.5 Sonnet**, demonstrating the core principles of **agentic AI**:

- 🧠 AI-driven planning  
- 🔗 Dynamic API orchestration  
- 🌍 Real-world data interaction  
- 📊 Intelligent summarization  

This project uses **Amazon Bedrock (us-west-2)** to access Claude 4.5 Sonnet and integrates with the official **National Weather Service (NWS) API** for live weather data.

---

# 🧠 What Makes This Agent *Agentic*?

This system demonstrates the three defining characteristics of agentic AI:

## 1️⃣ Autonomy
- Converts natural language locations into estimated coordinates
- Dynamically generates NWS Points API URLs
- Extracts Forecast API URLs from API responses
- Handles errors and unexpected failures

## 2️⃣ Reactivity
- Accepts cities, ZIP codes, states, or descriptive locations
- Adapts to different NWS API response structures
- Handles network timeouts and JSON parsing errors

## 3️⃣ Proactivity
- Plans API strategy from minimal input
- Executes sequential API calls (Points → Forecast)
- Summarizes raw JSON into human-readable insights
- Formats actionable weather information

---

# 🏗️ Architecture Overview

```text
User Input
   ↓
Claude 4.5 Sonnet (Amazon Bedrock)
   ↓
Generate NWS Points API URL
   ↓
Execute Points API (curl)
   ↓
Extract Forecast URL
   ↓
Execute Forecast API (curl)
   ↓
Claude Processes Raw JSON
   ↓
Human-Readable Weather Summary
```
---

# ☁️ AI Infrastructure
Model Access

Service: Amazon Bedrock

Region: us-west-2

Model ID: us.anthropic.claude-sonnet-4-5-20250929-v1:0

API Method: bedrock.converse()

# Inference Configuration
```code
inferenceConfig = {
    "maxTokens": 2000,
    "temperature": 0.7
}
```

- maxTokens:  controls maximum response length

- temperature: controls creativity vs determinism

# 🌍 Weather Data Source

Powered by the official API:

🔗 https://api.weather.gov

---

## API Workflow

### 1️⃣ Generate Points API
https://api.weather.gov/points/{lat},{lon}


### 2️⃣ Extract Forecast URL  
Extract the `forecast` URL from the Points API JSON response.

### 3️⃣ Execute Forecast API  
Call the extracted Forecast API endpoint to retrieve detailed weather data.

### 4️⃣ Summarize with Claude  
Send the raw forecast JSON to Claude 4.5 Sonnet for intelligent summarization and formatting.

# Env Requirements

- Python 3.10+
- AWS account with Bedrock access enabled
- Claude 4.5 Sonnet enabled in Bedrock
- AWS credentials configured locally
- curl installed on your machine
- Run 'aws configure' to configure the environment
- IAM Role permissions required - bedrock:InvokeModel and bedrock:Converse

# 🚀 Running the Agent

This project includes two versions of your AI Weather Agent:

### Run cli version

```bash
python weather_agent_cli.py
```

### Run web version

```bash
streamlit run weather_agent_web.py
```

