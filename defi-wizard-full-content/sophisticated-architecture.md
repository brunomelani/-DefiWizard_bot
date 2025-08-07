---
description: >-
  🧙‍♂️ Explore @DefiWizard_bot under the hood and enjoy the view of navigating
  thru the defi on a v8
---

# 🫂 Sophisticated Architecture

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Defi Wizard Agent swarm v2.0</p></figcaption></figure>

***

### 🧠 Sophisticated AI Guild Architecture

_Also known as the AI Swarm System_

At the core of **Defi Wizard** is a highly modular **agent swarm architecture**, where each component plays a specialized role. Powered by **n8n**, this system is orchestrated to maximize data quality, minimize latency, and deliver sharp, multi-layered DeFi insights — all within seconds.

***

#### 🧱 1. The Frontliner (Metadata Commander)

**🔍 Purpose:**\
Serves as the gateway for resolving any token query, enriching context for downstream agents.

**🛠️ Core Functions:**

* Resolves token identity via **name, ticker, or contract address**
* Validates **network compatibility** across 100+ chains
* Fetches token metadata: **market cap, 24h volume, creation date, socials, and chain info**
* Aggregates data from **GeckoTerminal** and **DexScreener**
* Outputs a clean, structured **JSON payload** for the Master Orchestrator

**💡 Impact:**\
Guarantees all downstream agents receive **high-integrity, pre-validated data**, increasing system speed, accuracy, and coherence.

***

#### 🧙‍♂️ 2. @DefiWizard\_bot (Master Orchestrator)

**🧠 Purpose:**\
Acts as the central AI coordinator — the "brain" of the swarm.

**⚙️ Core Functions:**

* Interprets user intent
* Delegates subtasks to relevant sub-agents
* Synthesizes and formats **multi-dimensional insights** into actionable responses
* Delivers **HTML-rich Telegram outputs** that are clean and professional

**⚡ Key Features:**

* Smart task allocation to **reduce redundant API calls**
* Balances CEX, DEX, technical, and social data into unified responses
* Built-in **rate limit intelligence** to avoid API lockouts

***

#### 🧩 3. Specialized Sub-Agents

Each sub-agent focuses on a specific data domain and executes tasks in parallel:

**🏦 CEX Sub-Agent**

* Fetches CEX data (price, volume, trends) from **CoinGecko MCP**
* Specializes in **blue-chip tokens** and widely-listed assets

**🦄 DEX Sub-Agent**

* Retrieves DEX token and pool data across **200+ chains and 1,600+ DEXs**
* Capable of **batching up to 30 tokens per API call**, ensuring scalability

**📊 TA Agent Master**

* Conducts **multi-timeframe technical analysis**
* Splits into **3 sub-agents** to handle multiple timeframes (e.g., 15m, 1h, 4h, 1d) simultaneously
* Uses **GeckoTerminal** + **Syve.ai** for OHLCV data
  * Up to **2,500 candles** (Base/Ethereum)
  * Up to **1,000 candles or 6 months** for other chains

**🐦 Twitter X Agent**

* Evaluates Twitter activity for **influencer behavior**, **community engagement**, and **sentiment quality**
* Flags red flags like **bot-like engagement**, **giveaway spam**, or **fake blue checks**

***

#### 🔮 Future Sub-Agents (Planned)

* **🛡 Token Security Specialist** – Automated contract auditing via **GoPlus API**
* **🌍 Social Sentiment Analyst** – Cross-platform narrative detection (Discord, Telegram, YouTube)

***

### ⚙️ Workflow Precision

**🧪 Metadata Enrichment**\
Frontliner ensures all agents begin with a clean, structured context, avoiding overlap and boosting task accuracy.

**🧠 Memory Management**\
Maintains limited conversational memory (last 5 messages) for session continuity. _(Session context engine upgrade in progress.)_

**🔁 Robust Error Handling**\
Retries and fallback logic for failed API calls ensures response consistency.

**📉 Rate Limit Optimization**\
Smart request pacing and batching keep all agents within their provider limits.

***

### 🧵 Example Workflow:

**User:** “Analyze $WIF on Solana”\
**Process:**

1. **Frontliner:**\
   Resolves `$WIF`, confirms **Solana**, fetches:
   * Market Cap: $20M
   * 24h Volume: $5M
   * Creation Date: 2024‑01‑15
   * Socials & Chain Metadata
2. **@DefiWizard\_bot:**\
   Delegates tasks to sub-agents:
   * **CoinGecko MCP:** CEX price/volume trends
   * **GeckoTerminal:** DEX pools + liquidity
   * **TA Agent Master:** 1h and 4h technical analysis
   * **Twitter X Agent:** Sentiment and community quality check
3. **Response Delivered to Telegram:**\
   A fully formatted HTML message, with clean market positioning and alpha insights — all orchestrated in under 10 seconds.
