# MCP Server Replicate

[![Python Version](https://img.shields.io/badge/python-3.11%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Type Checker](https://img.shields.io/badge/type%20checker-mypy-blue.svg)](https://github.com/python/mypy)
[![Ruff](https://img.shields.io/badge/linter-ruff-red.svg)](https://github.com/astral-sh/ruff)
[![PyPI version](https://badge.fury.io/py/mcp-server-replicate.svg)](https://pypi.org/project/mcp-server-replicate/)
[![smithery badge](https://smithery.ai/badge/@gerred/mcp-server-replicate)](https://smithery.ai/server/@gerred/mcp-server-replicate)

A FastMCP server implementation for the Replicate API, providing resource-based access to AI model inference with a focus on image generation.

<a href="https://glama.ai/mcp/servers/r830bzsk7r"><img width="380" height="200" src="https://glama.ai/mcp/servers/r830bzsk7r/badge" alt="Server Replicate MCP server" /></a>

## Features

- 🖼️ Resource-based image generation and management
- 🔄 Real-time updates through subscriptions
- 📝 Template-driven parameter configuration
- 🔍 Comprehensive model discovery and selection
- 🪝 Webhook integration for external notifications
- 🎨 Quality and style presets for optimal results
- 📊 Progress tracking and status monitoring
- 🔒 Secure API key management

## Available Prompts

The server provides several specialized prompts for different tasks:

### Text to Image (Primary)

Our most thoroughly tested and robust prompt. Optimized for generating high-quality images from text descriptions with:

- Detailed style control
- Quality presets (draft, balanced, quality, extreme)
- Size and aspect ratio customization
- Progress tracking and real-time updates

Example:

```
Create a photorealistic mountain landscape at sunset with snow-capped peaks, quality level: quality, style: photorealistic
```

### Other Prompts

- **Image to Image**: Transform existing images (coming soon)
- **Model Selection**: Get help choosing the right model for your task
- **Parameter Help**: Understand and configure model parameters

## Prerequisites

- Python 3.11 or higher
- A Replicate API key (get one at https://replicate.com/account)
- [UV](https://github.com/astral-sh/uv) for dependency management

## Installation

### Installing via Smithery

To install MCP Server Replicate for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@gerred/mcp-server-replicate):

```bash
npx -y @smithery/cli install @gerred/mcp-server-replicate --client claude
```

### Installing Manually
You can install the package directly from PyPI:

```bash
# Using UV (recommended)
uv pip install mcp-server-replicate

# Using UVX for isolated environments
uvx install mcp-server-replicate

# Using pip
pip install mcp-server-replicate
```

## Claude Desktop Integration

1. Make sure you have the latest version of Claude Desktop installed
2. Open your Claude Desktop configuration:

```bash
# macOS
code ~/Library/Application\ Support/Claude/claude_desktop_config.json

# Windows
code %APPDATA%\Claude\claude_desktop_config.json
```

3. Add the server configuration using one of these options:

```json
{
  "globalShortcut": "Shift+Alt+A",
  "mcpServers": {
    "replicate": {
      "command": "uv",
      "args": ["tool", "run", "mcp-server-replicate"],
      "env": {
        "REPLICATE_API_TOKEN": "APITOKEN"
      },
      "cwd": "$PATH_TO_REPO"
    }
  }
}
```

4. Set your Replicate API key:

```bash
# Option 1: Set in your environment
export REPLICATE_API_TOKEN=your_api_key_here

# Option 2: Create a .env file in your home directory
echo "REPLICATE_API_TOKEN=your_api_key_here" > ~/.env
```

5. Restart Claude Desktop completely

You should now see the 🔨 icon in Claude Desktop, indicating that the MCP server is available.

## Usage

Once connected to Claude Desktop, you can:

1. Generate images with natural language:

   ```
   Create a photorealistic mountain landscape at sunset with snow-capped peaks
   ```

2. Browse your generations:

   ```
   Show me my recent image generations
   ```

3. Search through generations:

   ```
   Find my landscape generations
   ```

4. Check generation status:
   ```
   What's the status of my last generation?
   ```

## Troubleshooting

### Server not showing up in Claude Desktop

1. Check the Claude Desktop logs:

```bash
tail -n 20 -f ~/Library/Logs/Claude/mcp*.log
```

2. Verify your configuration:

- Make sure the path in `claude_desktop_config.json` is absolute
- Ensure UV is installed and in your PATH
- Check that your Replicate API key is set

3. Try restarting Claude Desktop

For more detailed troubleshooting, see our [Debugging Guide](docs/debugging.md).

## Documentation

- [Implementation Plan](PLAN.md)
- [Contributing Guide](CONTRIBUTING.md)
- [API Reference](docs/api.md)
- [Resource System](docs/resources.md)
- [Template System](docs/templates.md)

## Development

1. Clone the repository:

```bash
git clone https://github.com/gerred/mcp-server-replicate.git
cd mcp-server-replicate
```

2. Install development dependencies:

```bash
uv pip install --system ".[dev]"
```

3. Install pre-commit hooks:

```bash
pre-commit install
```

4. Run tests:

```bash
pytest
```

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
