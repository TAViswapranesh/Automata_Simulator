# Automata Simulator

A comprehensive, web-based tool for simulating and visualizing various types of Automata. This simulator supports **Deterministic Finite Automata (DFA)**, **Non-deterministic Finite Automata (NFA)**, and **Pushdown Automata (PDA)**.

## 🚀 Features

- **Interactive transition diagrams** powered by [vis-network](https://visjs.github.io/vis-network/).
- **Multi-machine support**:
  - **DFA**: Standard deterministic processing.
  - **NFA**: Non-deterministic processing with support for multiple simultaneous states.
  - **PDA**: Stack-based automata with custom pop/push actions.
- **Visual Tracing**: See the exact path your input string takes through the states.
- **Dynamic Visualization**: Merged transition labels for a clean, readable diagram.
- **Responsive Web Interface**: Simple and intuitive design for experimentation.

## 🛠️ Usage Guide

To use the simulator, you need to provide the following inputs:

1. **States**: A comma-separated list of state names (e.g., `q0,q1,q2`).
2. **Start State**: The name of the initial state (e.g., `q0`).
3. **Final States**: A comma-separated list of accepting states (e.g., `q1,q2`).
4. **Transitions**: A specialized JSON format (detailed below).
5. **Input String**: The string you want to simulate (e.g., `0101`).

### Transition Formats

#### Deterministic Finite Automata (DFA)
Each state maps symbols to a single target state.
```json
{
  "q0": {"0": "q0", "1": "q1"},
  "q1": {"0": "q2", "1": "q1"},
  "q2": {"0": "q0", "1": "q1"}
}
```

#### Non-deterministic Finite Automata (NFA)
Each state can map symbols to multiple target states (comma-separated).
```json
{
  "q0": {"0": "q0", "1": "q0,q1"},
  "q1": {"0": "q2"},
  "q2": {}
}
```

#### Pushdown Automata (PDA)
Each state maps symbols to a `targetState,action` pair.
- Actions can be: `pop`, `nop` (no action), or any character to `push` (e.g., `A`).
```json
{
  "q0": {"a": "q0,A", "b": "q1,pop"},
  "q1": {"b": "q1,pop"}
}
```

## 🏗️ Technical Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript.
- **Visualization**: [vis-network](https://unpkg.com/vis-network/standalone/umd/vis-network.min.js).
- **Architecture**: Client-side only (no backend required).

## 📄 License
This project is open-source. Feel free to use and modify it for educational purposes.
