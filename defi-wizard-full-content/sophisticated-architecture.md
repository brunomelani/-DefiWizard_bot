---
description: >-
  🧙‍♂️ Explore @DefiWizard_bot under the hood and enjoy the view of navigating
  thru the defi on a v8
---

# 🫂 Sophisticated Architecture

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Defi Wizard Agent swarm v2.0</p></figcaption></figure>

***

#### 1. The Frontliner

* **Purpose**: Collects foundational token metadata to streamline analysis.
* **Function**:
  * Resolves token identities (name, ticker, or contract address) and validates network compatibility.&#x20;
  * Fetches market cap, 24h volume, creation time, social links, and chain data via multiple APIs to enrich master orchestrator agent with enough context.
  * Outputs enriched JSON (e.g., token\_id, chain, mc, volume, socials) for the orchestrator.
* **Impact**: Ensures sub-agents start with high-quality, structured data, boosting efficiency and accuracy.

#### 2. @DefiWizard\_bot (Master Orchestrator)

* **Purpose**: Coordinates the agent swarm to deliver comprehensive insights.
* **Function**:
  * Delegates tasks to sub-agents based on query intent and The Frontliner’s metadata.
  * Synthesizes results into actionable recommendations.
  * Formats Telegram responses in HTML for clarity and professionalism.
* **Key Features**:
  * Optimizes task allocation to minimize API calls and respect rate limits.
  * Seamlessly integrates market, technical, and social data.

#### 3. Specialized Sub-Agents

* **CEX Subagent**:
  * Retrieves CEX market data (prices, volume, trends).
  * Manages blue chips and bigger coins present on Coingecko.
*   **DEX Subagent**:

    * Extracts DEX token/pool data across 200+ networks and 1,600+ DEXs.
    * Batches up to 30 tokens per call for scalability.


* **TA Agent Master**:
  * Conducts multi-timeframe technical analysis using 3 sub agents to process 3 different OLHCv timeframes in multiple API calls simultaneously  (Ethereum/Base) up to 2500 candles and Other chains OHLCV limited to 1000 candles or 6months data.
  * Delegates timeframes to sub-agents for parallel processing.
*   **Twitter X Agent**:

    * Analyzes Twitter activity for sentiment, influencer patterns, and community quality.
    * Flags risks like giveaway spam or bot accounts.


* **Future Sub-Agents** (In Development):
  * Token Security Specialist: Contract audits via GoPlus API.
  * Social Sentiment Analyst: Multi-platform narrative analysis.

#### Workflow Precision

* **Metadata Enrichment**: The Frontliner’s initial data ensures sub-agents focus on specialized tasks, reducing redundancy.
* **Memory Management**: Uses last 5 messages context to maintain user session context.(to be improved)
* **Error Handling**: Implements retries and fallbacks for robust API interactions.
* **Rate Limit Optimization**: Coordinates requests to respect API limits and avoid errors.

#### Example Workflow

1. User sends: “Analyze $WIF on Solana” to @DefiWizard\_bot.
2. The Frontliner validates the token, confirms Solana network, and fetches metadata (market cap: $20M, volume: $5M, creation: 2024-01-15, socials).
3. @DefiWizard\_bot delegates:
   * CoinGecko MCP: CEX price and volume trends.
   * GeckoTerminal: DEX pool data and liquidity.
   * TA Agent: Price action on 1h and 4h timeframes.
   * Twitter X Agent: Sentiment and community signals.

