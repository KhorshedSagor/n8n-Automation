# n8n-Automation

Resource: https://www.youtube.com/watch?v=Ey18PDiaAYI

# **Structured Notes: Building AI Agents & Automations with n8n**  

## **Course Overview**  
- **Objective**: Transform beginners into proficient AI automation builders using **n8n** (no-code workflow automation tool).  
- **Key Outcomes**:  
  - Set up **AI agents** (autonomous AI systems) vs. **AI workflows** (linear automations).  
  - Connect APIs (OpenAI, Google, Pinecone, etc.).  
  - Build 15+ real-world automations (RAG chatbots, customer support, LinkedIn content, etc.).  

---

## **Section 1: AI Agents vs. AI Workflows**  
### **1.1 What is an AI Agent?**  
- **Definition**: An AI system that **autonomously makes decisions** using:  
  - **Brain** (LLM like GPT-4, Claude, Gemini).  
  - **Memory** (short/long-term context).  
  - **Instructions** (system prompts defining its role).  
  - **Tools** (integrations like Gmail, CRM, APIs).  
- **Example**: A customer support agent that decides when to research, email, or escalate.  

### **1.2 What is an AI Workflow?**  
- **Definition**: A **linear, step-by-step automation** (no decision-making).  
  - Fixed sequence (e.g., CRM lead → research → draft email → send).  
  - More reliable, cheaper, and easier to debug than agents.  
- **When to Use**: For predictable, repetitive tasks.  

### **1.3 Key Differences**  
| Feature          | AI Workflow              | AI Agent                  |  
|------------------|--------------------------|---------------------------|  
| **Decision-Making** | None (fixed steps)     | Autonomous (LLM decides)  |  
| **Flexibility**  | Low (rigid structure)    | High (adapts dynamically) |  
| **Cost**         | Lower (fewer LLM calls)  | Higher (more LLM usage)   |  
| **Use Case**     | CRM updates, scheduled tasks | Customer support, research |  

---

## **Section 2: n8n Fundamentals**  
### **2.1 Core Concepts**  
- **Workflows**: Visual pipelines (trigger → nodes → output).  
- **Nodes**: Building blocks (triggers, actions, AI, data transforms).  
- **Executions**: Each run of a workflow (tracked in n8n).  
- **JSON**: Primary data format (used for inputs/outputs).  

### **2.2 Key Nodes & Their Uses**  
1. **Triggers**: Start workflows (e.g., new email, form submission).  
2. **AI Nodes**: Call LLMs (OpenAI, Claude, etc.).  
3. **HTTP Requests**: Connect to APIs (Perplexity, Firecrawl, etc.).  
4. **Data Transformations**: Filter, reformat, or merge data.  

### **2.3 Data Types in n8n**  
- **String** (text)  
- **Number** (integer/decimal)  
- **Boolean** (true/false)  
- **Array** (list of items)  
- **Object** (key-value pairs, can be nested)  

---

## **Section 3: Step-by-Step Builds**  
### **3.1 RAG Pipeline & Chatbot**  
**Goal**: Build a chatbot that answers questions using a **Pinecone vector database**.  

<img width="849" height="440" alt="Screenshot 2025-08-16 at 2 44 50 AM" src="https://github.com/user-attachments/assets/d0b78c6d-28e5-4a7f-abca-f49821c5f825" />

**Steps**:  
1. **Trigger**: New file in Google Drive (FAQ document).  
2. **Process**:  
   - Extract text → split into chunks → store in Pinecone.  
3. **Chat Interface**:  
   - User asks a question → AI searches Pinecone → generates answer.  

**Key Tools**:  
- **Pinecone** (vector database)  
- **OpenAI Embeddings** (convert text to vectors)  
- **OpenRouter** (access multiple LLMs)  

### **3.2 Customer Support Automation**  
**Goal**: Auto-reply to customer emails using AI.  

<img width="678" height="368" alt="Screenshot 2025-08-16 at 2 47 25 AM" src="https://github.com/user-attachments/assets/fb9a9178-82db-4161-817a-338c352d4317" />


**Steps**:  
1. **Trigger**: New email in Gmail.  
2. **AI Classifier**: Is this a support request?  
3. **AI Agent**:  
   - Searches Pinecone for policies → drafts reply → sends via Gmail.  

### **3.3 LinkedIn Content Creator**  
**Goal**: Auto-generate posts + graphics.  

<img width="982" height="368" alt="Screenshot 2025-08-16 at 2 47 58 AM" src="https://github.com/user-attachments/assets/15adeec5-d0b3-48bd-8462-20936542e65b" />


**Steps**:  
1. **Trigger**: Scheduled daily or manual run.  
2. **Research**: Tavly (web search) → finds trending topics.  
3. **AI Agent**: Writes post + generates image (DALL·E).  
4. **Output**: Updates Google Sheet + emails draft.  

---

## **Section 4: APIs & HTTP Requests**  
### **4.1 What is an API?**  
- **Definition**: A way for two systems to communicate (like a waiter taking orders).  
- **Key Components**:  
  - **Endpoint** (URL for the API).  
  - **Method** (GET, POST, etc.).  
  - **Headers** (authentication, content type).  
  - **Body** (data sent to the API).  

### **4.2 Setting Up API Requests in n8n**  
1. **Find API Docs** (e.g., Perplexity, Firecrawl).  
2. **Use cURL Import** (auto-fills most settings).  
3. **Configure**:  
   - **Authentication** (API key in headers).  
   - **Parameters** (query, body).  

### **4.3 Common APIs Used**  
| API          | Use Case                          | Auth Method       |  
|--------------|-----------------------------------|-------------------|  
| **OpenAI**   | Text/image generation             | API Key           |  
| **Perplexity** | Real-time web research          | API Key (Bearer)  |  
| **Firecrawl** | Scrape & extract website data   | API Key (Bearer)  |  
| **Tavly**    | Web search for AI agents         | API Key           |  

---

## **Section 5: Advanced Topics**  
### **5.1 AI Agent Tools & Memory**  
- **Tools**: Give agents abilities (search, email, CRUD operations).  
- **Memory**: Maintain context across conversations.  

### **5.2 Webhooks**  
- **Definition**: Real-time triggers from external apps.  
- **Example**: Stripe payment → n8n workflow starts.  

### **5.3 Multi-Agent Systems**  
- **Use Case**: Complex tasks (e.g., one agent researches, another drafts, a third approves).  

---

### Tavily - web search for context API provider
### Firecrawl - Provides API for data scraping
### Apify - Data scraping tool

## **Key Takeaways for Revision**  
✅ **AI Workflows** = Fixed steps | **AI Agents** = Autonomous decisions.  
✅ **n8n Basics**: Workflows, nodes, JSON, executions.  
✅ **APIs**: Use cURL imports, headers for auth, body for data.  
✅ **Real-World Builds**: RAG chatbots, customer support, content automation.  
✅ **Advanced**: Memory, webhooks, multi-agent systems.  

This structured breakdown helps revise concepts without rewatching the video. Let me know if you'd like any section expanded! 🚀
