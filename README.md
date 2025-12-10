# Wraithlion
wraithlion GitHub Description  WRAITHLion is an AI-infused crypto bot with adaptive personas, adversary detection, and survival-first execution. It doesn’t follow trends. It hunts them.
WRAITHInject v1.0.0

Stealthy Intelligent Trading Bot Powered by Clarion AI + WRAITH

Version Python License

🎯 Philosophy: Survive, Adapt, Hunt

WRAITHInject combines the personality injection capabilities of Clarion AI with the adaptive trading strategies of WRAITH to create an intelligent trading bot that:

Survives: Prioritizes capital preservation with survival-first risk management
Adapts: Dynamically switches trading personalities based on market conditions
Hunts: Executes trades with intelligent, unpredictable behavior
✨ Key Features

🎭 Dynamic Trading Personalities

Aggressive Persona (Alpha Hunter): Maximum returns in favorable conditions
Defensive Persona (Guardian): Capital preservation in hostile markets
Neutral Persona (Strategist): Balanced approach for normal conditions
Scout Persona: Small probe trades for market intelligence
Personas automatically switch based on:

Market regime (trending/ranging/volatile/quiet)
Opponent-Awareness Score (OAS)
Survival Index
🧠 Clarion AI Integration

INTENSE Protocol: Advanced prompt engineering for decision enhancement
Intent Extraction: Analyzes market conditions and trading setups
Context Amplification: Enriches decisions with personality-driven insights
Signal Weighting: Prioritizes critical market signals
Safety Validation: Ensures decisions align with risk parameters
👁️ WRAITH Core Technologies

Regime Engine

Classifies markets into four states:

Trending: Strong directional movement
Ranging: Oscillating within boundaries
Volatile: High uncertainty and erratic movement
Quiet: Low activity and minimal movement
Opponent-Awareness Score (OAS)

Detects adversarial trading conditions:

Unusual slippage patterns (front-running detection)
Loss clustering (systematic exploitation)
Timing exploitation (execution delays)
Setup-specific failures (pattern recognition by adversaries)
Survival Index

Multi-factor health metric combining:

Current drawdown
Recent win rate
Position exposure
Adversarial activity (OAS)
Chaotic Discipline

Controlled randomization to prevent pattern exploitation:

Entry timing randomization
Position size variance
Exit level adjustments
Random trade skipping
🛡️ Survival-First Risk Management

Daily Kill-Switch: Automatic trading pause at daily loss limit
Maximum Drawdown Control: Hard stop at configured drawdown threshold
Dynamic Position Sizing: Adjusts size based on survival index and regime
Minimum Risk/Reward Enforcement: 1.5:1 default (configurable)
📊 Comprehensive Analytics

Overall performance metrics (Sharpe, Sortino, profit factor)
Persona-specific performance tracking
Regime-specific strategy analysis
OAS correlation analysis
Risk-adjusted returns
🏗️ Architecture

wraithinject/
├── main.py                         # Entry point
├── config.json                     # Unified configuration
├── modules/
│   ├── __init__.py
│   ├── personality_injection.py    # Clarion AI personality system
│   ├── regime_engine.py           # Market regime classification
│   ├── oas_score.py               # Opponent-awareness detection
│   ├── execution.py               # Master execution coordinator
│   ├── risk_control.py            # Risk management
│   └── analytics.py               # Performance tracking
├── personas/
│   └── (persona configuration files)
└── data/
    └── market_data.csv            # Historical data for backtesting
🚀 Quick Start

Installation

Clone the repository (from main project):
git clone https://github.com/your-org/sameasthedaybefore.git
cd sameasthedaybefore
Install dependencies:
pip install -r requirements.txt
Configure WRAITHInject: Edit wraithinject/config.json:
{
  "clarion": {
    "backend": "ollama",
    "model": "llama2",
    "use_intense_protocol": true
  },
  "risk": {
    "initial_balance": 10000,
    "max_position_size": 0.02,
    "max_daily_loss": 0.05,
    "max_drawdown": 0.25
  }
}
Running a Backtest

python wraithinject/main.py --mode backtest --config wraithinject/config.json
Required Data Format: CSV with columns: timestamp, open, high, low, close, volume

Running Live Trading

⚠️ WARNING: Test thoroughly before live trading!

python wraithinject/main.py --mode live --config wraithinject/config.json
Note: You must implement exchange API integration in main.py:

_fetch_market_data(): Connect to exchange for real-time data
_execute_trade(): Implement order execution via exchange API
Checking Status

python wraithinject/main.py --mode status
📖 Usage Guide

Understanding Persona Switching

WRAITHInject automatically selects the optimal trading persona:

# Defensive Mode Triggered When:
- Survival Index < 0.3
- OAS > 0.7
→ Switches to Guardian persona
→ Reduces position sizes by 50%
→ Tightens stop losses
→ May pause trading entirely

# Aggressive Mode Triggered When:
- Survival Index > 0.7
- OAS < 0.3
- Regime = Trending or Ranging
→ Switches to Alpha Hunter persona
→ Increases position sizes by 30%
→ Uses wider stops
→ Seeks momentum opportunities

# Scout Mode Triggered When:
- Uncertainty in regime classification
- Rising OAS levels
→ Sends small probe trades
→ Gathers market intelligence
→ Tests for adversarial activity
Interpreting OAS Levels

OAS Range	Level	Action	Position Size
0.0 - 0.3	Low	Normal trading	100%
0.3 - 0.7	Moderate	Increase entropy	70%
0.7 - 0.85	High	Defensive mode	40%
0.85 - 1.0	Critical	Pause trading	0%
Configuring Risk Parameters

Edit config.json risk section:

{
  "risk": {
    "initial_balance": 10000,
    "max_position_size": 0.02,        // 2% of account per trade
    "max_daily_loss": 0.05,           // 5% daily loss limit
    "max_drawdown": 0.25,             // 25% maximum drawdown
    "survival_index_threshold": 0.3,  // Below this = defensive mode
    "min_risk_reward": 1.5            // Minimum R:R ratio
  }
}
🔬 Advanced Features

Custom Trading Strategy

Replace the default strategy in modules/execution.py:

def _default_strategy_logic(self, df: pd.DataFrame, analysis: Dict) -> Optional[Dict]:
    """
    Implement your custom strategy here.

    Args:
        df: Market data DataFrame (OHLCV)
        analysis: Market analysis with regime, OAS, survival index

    Returns:
        Trade signal dictionary or None
    """
    # Your strategy logic here
    current_price = df['close'].iloc[-1]
    regime = analysis["regime"]["type"]

    # Example: Custom indicator-based signal
    if regime == "trending":
        # Your logic
        return {
            "direction": "long",
            "entry_price": current_price,
            "stop_loss": current_price * 0.98,
            "take_profit": current_price * 1.04,
            "setup_type": "custom_strategy",
            "position_size": 1.0,  # Will be adjusted by risk manager
            "urgency": 0.6
        }

    return None
Creating Custom Personas

Edit personas in modules/personality_injection.py:

custom_persona = TradingPersona(
    name="Scalper",
    persona_type=TradingPersonaType.AGGRESSIVE,
    risk_tolerance=0.70,
    decision_style="fast",
    preferred_regimes=["volatile", "ranging"],
    position_size_multiplier=0.8,
    stop_loss_multiplier=0.6,  # Tight stops
    hold_duration_preference="short"
)
Analyzing Performance

Access detailed analytics:

from modules.analytics import PerformanceAnalytics

analytics = PerformanceAnalytics()

# After trading
report = analytics.generate_comprehensive_report()

print(f"Win Rate: {report['overall_statistics']['win_rate']:.2%}")
print(f"Sharpe Ratio: {report['overall_statistics']['sharpe_ratio']:.2f}")
print(f"Max Drawdown: {report['overall_statistics']['max_drawdown']:.2%}")

# Persona performance
for persona, perf in report['persona_performance'].items():
    print(f"{persona}: {perf['total_pnl']:.4f}")

# Export to files
analytics.export_to_json("performance_report.json")
analytics.export_to_csv("trade_history.csv")
📊 Performance Metrics

WRAITHInject tracks comprehensive metrics:

Overall Statistics

Total trades, win rate, profit factor
Sharpe ratio, Sortino ratio
Maximum drawdown
Average trade duration
Risk-adjusted returns
Persona Analysis

Win rate by persona
Average PnL by persona
Sharpe ratio by persona
Best/worst trades per persona
Regime Analysis

Performance in each market regime
Regime suitability scores
Regime-specific profit factors
OAS Correlation

Performance at different OAS levels
Correlation between OAS and PnL
Adversarial event tracking
🔧 Configuration Reference

Clarion AI Settings

{
  "clarion": {
    "backend": "ollama",              // "openai", "anthropic", "ollama"
    "model": "llama2",                // Model name
    "use_intense_protocol": true,     // Enable INTENSE Protocol
    "temperature": 0.7,               // LLM temperature
    "max_tokens": 2048                // Max response tokens
  }
}
WRAITH Settings

{
  "wraith": {
    "regime_lookback": 100,           // Bars for regime classification
    "volatility_window": 20,          // Bars for volatility calc
    "pattern_memory": 100,            // Trades to remember for OAS
    "oas_threshold": 0.7,             // OAS defensive mode trigger
    "max_probes_per_day": 5           // Maximum probe trades daily
  }
}
Trading Settings

{
  "trading": {
    "default_persona": "neutral",     // Starting persona
    "auto_persona_switching": true,   // Enable dynamic switching
    "enable_probe_trades": true,      // Allow scout probes
    "enable_entropy_randomization": true,  // Chaotic discipline
    "position_size_variance": 0.1,    // Size randomization (±10%)
    "timing_variance": 0.15           // Timing randomization (±15%)
  }
}
🤝 Integration with Clarion AI

WRAITHInject leverages Clarion AI's core capabilities:

Personality Weaving: Trading personas use Clarion's PersonalityWeaver
INTENSE Protocol: Decision enhancement through:
Intent extraction from market conditions
Context amplification with trading expertise
Recursive enrichment of trade analysis
Signal weighting for critical factors
Safety Validation: OAS integrates with Clarion's safety framework
Multi-backend Support: Use OpenAI, Anthropic, or local Ollama models
🛡️ Safety & Risk Disclosure

⚠️ IMPORTANT DISCLAIMERS:

Trading Risk: Trading involves substantial risk of loss. Never trade with money you cannot afford to lose.
No Guarantees: Past performance does not guarantee future results. This bot can and will lose money.
Testing Required: Thoroughly backtest and paper trade before risking real capital.
Your Responsibility: You are solely responsible for your trading decisions and outcomes.
Not Financial Advice: WRAITHInject is a tool, not financial advice.
Recommended Safety Measures:

Start with paper trading
Use small position sizes initially
Monitor the bot closely
Set conservative risk limits
Have a manual kill-switch ready
📝 License

MIT License - See LICENSE file for details

🙏 Acknowledgments

Clarion AI: For providing the personality injection and INTENSE Protocol framework
WRAITH: For the adaptive trading and opponent-awareness concepts
Python Community: For the excellent ecosystem of trading libraries
📞 Support & Contributing

Issues: Report bugs or request features via GitHub Issues
Documentation: See /docs for detailed guides
Contributing: Pull requests welcome! Please read CONTRIBUTING.md first
Made with ❤️ for algorithmic traders who value survival as much as profits

"The best trader is not the one who makes the most money, but the one who survives the longest"
