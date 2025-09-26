# ATXP + Vercel AI SDK Demo

This example project demonstrates how to integrate ATXP's pay-per-use MCP (Model Context Protocol) tools with Vercel AI SDK for building AI applications. This example project accesses LLMs through the [ATXP LLM Gateway](https://docs.atxp.ai/). The LLM Gateway allows you to Access multiple LLM providers through a single, unified API without managing multiple accounts or API keys, giving you instant access to models from qwen, claude, deepseek, gemini, llama, gpt, grok, and more.

## Features

- **LLM Gateway Integration**: Access multiple LLM providers through ATXP's unified OpenAI-compatible API
- **Image Generation**: Create images using ATXP's image generation MCP server
- **Web Search**: Search for information using ATXP's search MCP server
- **Streaming Responses**: Leverage Vercel AI SDK for real-time AI interactions
- **Pay-per-use**: Only pay for what you use with ATXP's usage-based pricing

## Prerequisites

- Node.js 18.0.0 or higher
- An ATXP account with a connection string
- An OpenAI API key

## Setup

1. Create your own copy of this repo using [the template](https://github.com/new?template_name=atxp-vercel-demo&template_owner=atxp-dev)

2. Clone your newly created repo: 
   ```bash
   git clone git@github.com:your-github-user/your-new-repo
   cd your-new-repo
   ```

3. Install the needed dependencies:
    ```bash
    npm install
    ```

4. Copy the example environment file and add your credentials:

```bash
cp env.example .env
```

Edit `.env` and add your credentials:

```env
# Required for ATXP MCP tools (get from your ATXP dashboard)
# Create an ATXP Account at https://accounts.atxp.ai
ATXP_CONNECTION=https://accounts.atxp.ai?connection_token=<your_token>&account_id=<your_account_id>
```

If you aren't using the ATXP LLM Gateway, you'll also need to specify your OpenAI API Key:
```env
# Required for OpenAI integration
OPENAI_API_KEY=your_openai_api_key_here
```

**Important**: Never commit your `.env` file to version control. It's already added to `.gitignore`.

## Usage

1. Build the project
    ```bash
    npm run build
    ```

2. Run the compiled project from the root of your repo:
    Use the [ATXP Search MCP server](https://docs.atxp.ai/client/mcp_servers/search) to search the web:
    ```bash
    node dist/index.js "provide me with the latest news about AI"
    ```

    Use the [ATXP Image Generation MCP server](https://docs.atxp.ai/client/mcp_servers/image) to generate an image from a prompt:
    ```bash
    node dist/index.js "create an image of a tree."
    ```

## How It Works

This demo integrates ATXP's MCP tools with Vercel AI SDK through the following process:

1. **ATXP Account Initialization**: Creates an ATXP account using your connection string
2. **MCP Transport Setup**: Builds streamable transports for ATXP's MCP servers (image generation and search)
3. **Tool Integration**: Connects ATXP's MCP tools with Vercel AI SDK's experimental MCP client
4. **AI Processing**: Uses OpenAI's GPT models through the ATXP LLM Gateway with the integrated tools to process user requests
5. **Response Generation**: Returns structured responses with tool results

## Project Structure

```
atxp-vercel-demo/
├── src/
│   └── index.ts          # Main application logic
├── env.example           # Environment variables template
├── package.json          # Dependencies and scripts
├── tsconfig.json         # TypeScript configuration
└── README.md             # This file
```

## Key Dependencies

- `@atxp/client`: ATXP SDK for MCP tool integration
- `ai`: Vercel AI SDK for streaming AI applications
- `@ai-sdk/openai`: OpenAI integration for Vercel AI SDK
- `dotenv`: Environment variable management

## Extending the Demo

To add more ATXP MCP services:

1. Add a new service configuration to the `SERVICES` object in `src/index.ts`
2. Include the new service in the `services` array
3. Update the validation and help text as needed

## Documentation

- [ATXP LLM Gateway](https://docs.atxp.ai/llm) - Access multiple LLM providers through a unified API
- [ATXP Vercel AI SDK Integration Guide](https://docs.atxp.ai/client/guides/vercel_ai)
- [ATXP MCP Servers Documentation](https://docs.atxp.ai/client/mcp-servers)
- [Vercel AI SDK Documentation](https://sdk.vercel.ai/docs)

## Support

- Join the [ATXP Community on Discord](https://discord.gg/atxp)
- Check out the [ATXP Documentation](https://docs.atxp.ai/)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
