# Superagents

Superagents is a CLI tool and standards to supercharge your coding assistant (Claude Code, Cursor, etc) to be expert in building with your agent framework of choise (Agno, Mastra, etc) and structure your project with scenarios agent testing, evaluation notebooks, versioned prompts and observability instrumentation.

Superagents allow you to create agents with best practices baked in and ready for production.

### The Superagent Structure

```
my-agent-project/
├── app/ (or src/)           # The actual agent code, structured according to the chosen framework
├── tests/
│   ├── evaluations/         # Jupyter notebooks for evaluations
│   │   └── example_eval.ipynb
│   └── scenarios/           # End-to-end scenario tests
│       └── example_scenario.test.{py,ts}
├── prompts/                 # Versioned prompt files for team collaboration
│   └── sample_prompt.yaml
├── prompts.json             # Prompt registry
├── .mcp.json                # MCP server configuration
├── AGENTS.md                # Development guidelines
├── .env                     # Environment variables
└── .gitignore
```

The structure and guidelines on `AGENTS.md` ensure every new feature required for the coding assistant is properly tested, evaluated, and that the prompts are versioned.

The `.mcp.json` comes with all the right MCPs set up so you coding assistant becomes an expert in your framework of choice and know where to find new tools.

[`scenarios/`](https://github.com/langwatch/scenario) tests guarantee the agent behaves as expected, which simulates a conversation with the agent making sure it does what expected.

`evaluations/` notebooks holds dataset and notebooks for evaluating pieces of your agent pipeline such as a RAG or classification tasks it must do

Finally, `prompts/` hold all your versioned prompts in yaml format, synced and controlled by `prompts.json`, to allow for playground and team collaboration.

## Installation

```bash
npm install -g @langwatch/superagents
```

Or use with npx:

```bash
npx @langwatch/superagents init my-agent-project
```

## Documentation

- **[Quick Start](QUICKSTART.md)** - Get started in 2 minutes
- **[Walkthrough](examples/WALKTHROUGH.md)** - Detailed step-by-step guide
- **[Contributing](CONTRIBUTING.md)** - How to contribute to Superagents
- **[Changelog](CHANGELOG.md)** - Version history

## Usage

### Initialize a new project

```bash
# In current directory
superagents init .

# In a new directory
superagents init my-awesome-agent
```

The CLI will guide you through:

1. **Programming Language**: Python or TypeScript
2. **Agent Framework**: Agno (Python) or Mastra (TypeScript)
3. **Coding Assistant**: Claude Code, Cursor CLI, or Kilocode CLI
4. **LLM Provider**: OpenAI
5. **API Keys**: OpenAI and LangWatch
6. **Project Goal**: What you want to build

## Philosophy

Superagents promotes the **Agent Testing Pyramid** approach:

1. **Unit Tests** - Test deterministic components
2. **Evals & Optimization** - Measure and optimize probabilistic components
3. **Simulations** - End-to-end validation with Scenario

Learn more: https://scenario.langwatch.ai/best-practices/the-agent-testing-pyramid

## Key Features

### 🎯 Framework Integration

- **Agno**: Automatically downloads `.cursorrules` and `llms.txt`
- **Mastra**: Configures Mastra MCP for real-time documentation

### 🧪 LangWatch Integration

- **Prompt CLI**: Manage versioned prompts
- **Scenario Testing**: End-to-end agent testing
- **Evaluations**: Measure component performance
- **MCP Server**: Expert guidance built into your coding assistant

### 🤖 Coding Assistant Setup

Your coding assistant (e.g., Claude Code, Cursor CLI, Kilocode CLI) is:
- **Automatically launched** after project setup with initial prompt
- Pre-configured with framework-specific knowledge (via MCP or docs)
- Loaded with LangWatch best practices
- Equipped with prompt management expertise
- Set up with testing methodologies
- Auto-detected - the CLI shows which assistants are installed on your system

## Requirements

- Node.js 18+
- npm or pnpm
- A coding assistant CLI (one of the following):
  - [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code-agent) (`claude`)
  - [Cursor CLI](https://www.cursor.com/) (`cursor-agent`)
  - [Kilocode CLI](https://www.kilocode.ai/) (`kilocode`)
- API Keys:
  - OpenAI API key
  - LangWatch API key (get one at https://app.langwatch.ai/authorize)

## Development

```bash
# Clone the repo
git clone https://github.com/langwatch/superagents
cd superagents

# Install dependencies
pnpm install

# Run in development
pnpm dev init test-project

# Build
pnpm build
```

## Examples

### Python + Agno

```bash
superagents init trading-agent
# Select: Python, Agno, your preferred coding assistant, OpenAI
# Goal: "Build an agent that can analyze stock prices and provide trading recommendations"
```

### TypeScript + Mastra

```bash
superagents init customer-support
# Select: TypeScript, Mastra, your preferred coding assistant, OpenAI
# Goal: "Build a customer support agent that can handle common queries and escalate complex issues"
```

### Coding Assistant Auto-Launch

After project setup completes, Superagents **automatically launches** your chosen coding assistant with a customized initial prompt that includes:
- Your project goal
- Framework-specific context
- Best practices guidance
- Next steps to get started

The CLI detects which coding assistants are installed on your system and shows installed options first in the selection menu. Not installed assistants appear in gray with "(not installed)" but can still be selected.

## Resources

- [LangWatch](https://langwatch.ai)
- [Scenario Documentation](https://scenario.langwatch.ai/)
- [Agent Testing Pyramid](https://scenario.langwatch.ai/best-practices/the-agent-testing-pyramid)
- [Agno](https://agno.com)
- [Mastra](https://mastra.ai)

## License

MIT

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

---

Built with ❤️ by the LangWatch team

