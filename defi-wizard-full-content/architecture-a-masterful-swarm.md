---
description: >-
  @DefiWizard_bot power lies in its meticulously designed, modular architecture.
  From the foundation agent to the orchestrator that directs a swarm of
  specialized agents for unparalleled efficiency.
---

# 🫂 Architecture: A Masterful Swarm

#### 1. The Frontliner

* **Purpose**: Collects foundational token metadata to streamline analysis.
* **Function**:
  * Resolves token identities (name, ticker, or contract address) and validates network compatibility (e.g., Ethereum’s 42-char 0x, Solana’s Base58, Sui’s 66-char 0x).
  * Fetches market cap, 24h volume, creation time, social links, and chain data using GeckoTerminal and DexScreener APIs.
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

* **CoinGecko MCP Subagent**:
  * Retrieves CEX market data (prices, volume, trends).
  * Manages 30/min rate limits for efficiency.
* **GeckoTerminal DEX Subagent**:
  * Extracts DEX token/pool data across 200+ networks and 1,600+ DEXs.
  * Batches up to 30 tokens per call for scalability.
* **TA Agent Master**:
  * Conducts multi-timeframe technical analysis using Syve.ai (Ethereum/Base) and GeckoTerminal OHLCV.
  * Delegates timeframes to sub-agents for parallel processing.
* **Twitter X Agent**:
  * Analyzes Twitter activity for sentiment, influencer patterns, and community quality.
  * Flags risks like giveaway spam or bot accounts.
* **Future Sub-Agents** (In Development):
  * Token Security Specialist: Contract audits via GoPlus API.
  * Social Sentiment Analyst: Multi-platform narrative analysis.

#### 4. Workflow Precision

* **Metadata Enrichment**: The Frontliner’s initial data ensures sub-agents focus on specialized tasks, reducing redundancy.
* **Memory Management**: Uses memoryBufferWindow nodes to maintain user session context.
* **Error Handling**: Implements retries and fallbacks for robust API interactions.
* **Rate Limit Optimization**: Coordinates requests to respect API limits (e.g., 30/min for GeckoTerminal, CoinGecko).

#### Example Workflow

1. User sends: “Analyze $WIF on Solana” to @DefiWizard\_bot.
2. The Frontliner validates the token, confirms Solana network, and fetches metadata (market cap: $20M, volume: $5M, creation: 2024-01-15, socials).
3. @DefiWizard\_bot delegates:
   * CoinGecko MCP: CEX price and volume trends.
   * GeckoTerminal: DEX pool data and liquidity.
   * TA Agent: Price action on 1h and 4h timeframes.
   * Twitter X Agent: Sentiment and community signals.
4. Orchestrator synthesizes results into a Telegram response:text`<b>WIF ($WIF)</b> 📍 Solana • 🦄 DEX: $0.02 | 💰 MC: $20M 💹 <b>Market Intelligence:</b> Volume surged 30% in 24h. 🛡️ <b>Risk Level:</b> High 📊 <b>Liquidity:</b> $1M | 👥 <b>Holders:</b> 10,000 🧙‍♂️ <b>Technical Analysis:</b> 4h RSI overbought, potential pullback to $0.018. 🌐 <b>Social Intelligence:</b> Strong influencer backing, but watch for pump-and-dump risks. 🎯 <b>Master Assessment:</b> Wait for dip to $0.018, target $0.025. 🧙‍♂️ Powered by @DefiWizard_bot`
