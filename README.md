# llm-bedrock-converse

LLM plugin for AWS Bedrock using the Converse API with full tool calling support.

## Features

- ✅ Tool calling / function calling support
- ✅ Works with MCP servers via llm-tools-mcp
- ✅ Streaming responses
- ✅ Conversation history
- ✅ Multi-modal (images, PDFs, videos)
- ✅ All Claude models on Bedrock
- ✅ Cross-region inference profiles

## Installation

```bash
llm install llm-bedrock-converse
```

## Configuration

Uses standard AWS credentials (boto3). Set region via environment variable:

```bash
export AWS_REGION=us-east-1
```

Or use AWS CLI default credentials.

## Usage

### Basic prompting

```bash
llm -m bedrock-converse/claude-3-haiku "Hello"
```

### With tool calling

```bash
# Built-in tools
llm -m bedrock-converse/claude-3-haiku -T llm_time "What time is it?"

# MCP servers (requires llm-tools-mcp)
llm -m bedrock-converse/claude-3-haiku -T MCP "What time is it in Tokyo?"

# Custom functions
llm -m bedrock-converse/claude-3-haiku --functions 'def add(a: int, b: int): return a + b' "What is 5+7?"
```

### Chat mode

```bash
llm chat -m bedrock-converse/claude-3-haiku
```

## Available Models

All models support tool calling via Converse API:

- `anthropic.claude-3-haiku-20240307-v1:0` (alias: `bedrock-converse/claude-3-haiku`, `bc-haiku`)
- `anthropic.claude-3-5-haiku-20241022-v1:0` (alias: `bedrock-converse/claude-3.5-haiku`, `bc-haiku-3.5`)
- `anthropic.claude-3-sonnet-20240229-v1:0` (alias: `bedrock-converse/claude-3-sonnet`, `bc-sonnet`)
- `anthropic.claude-3-5-sonnet-20240620-v1:0` (alias: `bedrock-converse/claude-3.5-sonnet`, `bc-sonnet-3.5`)
- `anthropic.claude-3-7-sonnet-20250219-v1:0` (alias: `bedrock-converse/claude-3.7-sonnet`, `bc-sonnet-3.7`)
- `anthropic.claude-3-opus-20240229-v1:0` (alias: `bedrock-converse/claude-3-opus`, `bc-opus`)
- `anthropic.claude-sonnet-4-20250514-v1:0` (alias: `bedrock-converse/claude-4-sonnet`, `bc-sonnet-4`)
- `anthropic.claude-sonnet-4-5-20250929-v1:0` (alias: `bedrock-converse/claude-4.5-sonnet`, `bc-sonnet-4.5`)
- `anthropic.claude-opus-4-20250514-v1:0` (alias: `bedrock-converse/claude-4-opus`, `bc-opus-4`)
- `anthropic.claude-opus-4-1-20250805-v1:0` (alias: `bedrock-converse/claude-4.1-opus`, `bc-opus-4.1`)
- `anthropic.claude-haiku-4-5-20251001-v1:0` (alias: `bedrock-converse/claude-4.5-haiku`, `bc-haiku-4.5`)

Cross-region models (us. prefix):
- `us.anthropic.claude-3-5-sonnet-20241022-v2:0` (alias: `bc-sonnet-3.5-v2`)
- `us.anthropic.claude-sonnet-4-5-20250929-v1:0` (alias: `bc-sonnet-4.5-us`)
- `us.anthropic.claude-opus-4-1-20250805-v1:0` (alias: `bc-opus-4.1-us`)

Global models (global. prefix):
- `global.anthropic.claude-sonnet-4-20250514-v1:0` (alias: `bc-sonnet-4-global`)
- `global.anthropic.claude-sonnet-4-5-20250929-v1:0` (alias: `bc-sonnet-4.5-global`)

## License

Apache-2.0
