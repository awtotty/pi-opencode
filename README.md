# pi-opencode

Extension for the [pi](https://github.com/mariozechner/pi-coding-agent) coding agent to add OpenCode as a provider. 🙂

## Features

- **40+ models**: GPT, Claude, Gemini, GLM, Kimi, Qwen, MiniMax, and more
- **opencode-go**: Subscription service (https://opencode.ai/zen/go)
- **opencode-zen**: Pay-as-you-go (https://opencode.ai/zen)

## Prerequisites

- You already have the [pi](https://github.com/earendil-works/pi) coding agent installed.
- You have an OpenCode account: https://opencode.ai/auth 

## Installation

### Option 1: Git URL (Recommended)

Add to your pi `settings.json` (`~/.pi/agent/settings.json`):

```json
{
  "packages": [
    "git:https://github.com/ShalokShalom/pi-opencode.git"
  ]
}
```

### Option 2: Clone locally

```bash
git clone https://github.com/ShalokShalom/pi-opencode.git ~/.pi/agent/extensions/pi-opencode
```

## Configuration

### 1. Get your API key

1. Sign up at https://opencode.ai/auth
2. Pay for the service via the billing menu
3. Copy your API key

### 2. Set the environment variable

Add this line to the shell config (`~/.bashrc`, `~/.zshrc`, `~/.config/fish/config.fish`)

Bash, Zsh, etc

```bash
export OPENCODE_API_KEY="your-api-key-here"
```

Fish

```fish
set -Ux OPENCODE_API_KEY "your-api-key-here"
```

### 3. Open pi

**First**, open a new shell to load the config (`exec bash`, `exec zsh`, `exec fish`).  
**Now** open `pi`.

## Usage

### Select a provider and model

Type `/model` to select a model. 

You can also select one directly via the full path:

```bash
/model opencode-zen/gpt-5.1
/model opencode-go-anthropic/minimax-m2.7
```

## Recommended Configuration

```
{
  "packages": [
    "git:https://github.com/ShalokShalom/pi-opencode.git"
  ],
  "defaultProvider": "opencode-go",
  "defaultModel": "deepseek-v4-flash"
}
```

### Available Providers

MiniMax M2.7 and M2.5 use the Anthropic Messages API.  
All other models use the OpenAI Chat Completions.

| Provider | API | Endpoint |
|----------|-----|----------|
| opencode-go | OpenAI Chat Completions | https://opencode.ai/zen/go/v1/chat/completions |
| opencode-zen | OpenAI Chat Completions | https://opencode.ai/zen/v1/chat/completions |
| opencode-go-anthropic | Anthropic Messages | https://opencode.ai/zen/go/v1/messages |
| opencode-zen-anthropic | Anthropic Messages | https://opencode.ai/zen/v1/messages |

## Troubleshooting

### "No API key" error

```bash
echo $OPENCODE_API_KEY
```

If empty, set it as shown in [step 2](#2-set-the-environment-variable)

### Extension not loading

Run `/reload` after changes.

### Model not found

Verify that the model name is correct; they are case-sensitive.

## Development

```bash
# Clone the repository
git clone https://github.com/awtotty/pi-opencode.git
cd pi-opencode

# Test locally
pi -e ./src/index.ts
```

## License

MIT

## Links

- [pi coding agent](https://github.com/mariozechner/pi-coding-agent)
- [OpenCode Go](https://opencode.ai/docs/go/)
- [OpenCode Zen](https://opencode.ai/docs/zen/)
- [OpenCode](https://opencode.ai/auth)
