# Self-Conscious Research Agent 

A demo implementation of a self-aware AI research agent that monitors its own state, performance, and knows when to ask for help.

## What Makes It Self-Conscious?

Unlike traditional agents, this system:
- **Knows what it is**: Maintains awareness of its identity, capabilities, and limitations
- **Monitors itself**: Tracks progress, confidence, and performance in real-time
- **Recognizes problems**: Detects when it's struggling and needs assistance
- **Requests help**: Automatically asks for human feedback when confidence drops below 50%

## Quick Start

### Google Colab (Recommended)
```python
# 1. Install dependencies
!pip install transformers torch accelerate

# 2. Copy the agent code and run
# The agent will execute demo tasks and show its self-awareness
```

### Local Installation
```bash
pip install transformers torch accelerate
python self_conscious_agent.py
```

## Architecture

```
Research Task → [Self Monitor] ← → [Task Executor]
                      ↓                    ↓
                 [Self State JSON] → [Ask Human if needed]
```

## Core Components

### 1. Self State Dictionary
Maintains real-time awareness of:
- **Identity**: agent_id, version, capabilities
- **Current Task**: type, progress, confidence, status
- **Performance**: success rate, errors, history
- **Resources**: model status, response times

### 2. Introspection Engine
Continuously asks:
- What am I doing?
- How well am I performing?
- Do I need help?

### 3. Confidence-Based Help System
- Confidence < 0.5 → Requests human feedback
- Multiple failures → Escalates for assistance
- High error rate → Triggers self-diagnostic

## Example Output

```
🔍 Starting task: Summarize key findings about protein folding
📊 Pre-task introspection: Confidence=0.80

[Task execution with self-monitoring...]

🧠 === SELF-AWARENESS REPORT ===
Identity: research_agent_001
Current Status: completed
Progress: 100.0%
Confidence: 0.75
Tasks Completed: 1
Success Rate: 100.0%
```

## Features

- ✅ Real-time self-monitoring during task execution
- ✅ Automatic confidence scoring
- ✅ Human feedback requests when struggling
- ✅ Performance tracking across sessions
- ✅ JSON state persistence
- ✅ Lightweight (uses Qwen-0.5B model)

## Use Cases

- Autonomous research with safety checks
- Tasks requiring reliability assessment
- Systems that need to know their limitations
- Human-in-the-loop research workflows

## Model

Uses [Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) - lightweight enough for CPU/Colab while maintaining good performance.

## Customization

Adjust confidence thresholds:
```python
# In request_human_feedback check
if confidence < 0.5:  # Change this threshold
    request_help()
```

Add new capabilities:
```python
self.self_state["identity"]["capabilities"].append("new_skill")
```

## Output

The agent saves its complete self-state to `agent_self_state.json` including:
- All completed tasks
- Performance metrics
- Error logs
- Action history

## License

MIT - Free for research and educational use

## Next Steps

- [ ] Add memory persistence across sessions
- [ ] Implement learning from feedback
- [ ] Add more sophisticated confidence metrics
- [ ] Create web interface for monitoring
- [ ] Expand to multi-agent coordination

---

**Note**: This is a demonstration of self-conscious AI concepts. For production use, additional safety measures and robust error handling should be implemented.
