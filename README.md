# MCP Server with HTTP Transport

This is a Model Context Protocol (MCP) server that uses HTTP transport instead of stdio. The server provides tools and resources for managing users.

## Features

- **Tools**: Create users, create random users with fake data
- **Resources**: Access user data via URIs
- **Prompts**: Generate fake user data
- **HTTP Transport**: Uses Streamable HTTP transport for communication

## Setup

1. Install dependencies:
```bash
npm install
```

2. Build the server:
```bash
npm run server:build
```

3. Run the server:
```bash
npm run server:dev
```

## Transport Configuration

The server is configured to use `StreamableHTTPServerTransport` instead of stdio. This allows the MCP server to communicate over HTTP, making it suitable for web-based clients and remote connections.

### Key Changes Made

1. **Import Change**: Switched from `StdioServerTransport` to `StreamableHTTPServerTransport`
2. **Configuration**: Added `sessionIdGenerator` for unique session management
3. **Crypto Import**: Added `node:crypto` for UUID generation

### Usage with MCP Clients

When connecting to this server, clients should use the HTTP transport configuration. The server will handle session management automatically using the provided session ID generator.

## Available Tools

- `create-user`: Create a new user with name, email, address, and phone
- `create-random-user`: Generate and create a user with fake data

## Available Resources

- `users://all`: Get all users data
- `users://{userId}/profile`: Get specific user details

## Development

- `npm run server:dev`: Run in development mode with hot reload
- `npm run server:build`: Build the TypeScript code
- `npx @modelcontextprotocol/inspector`: Run the MCP inspector for testing
    - Take the `Session token` from the command-line and insert it into the Configuration->Proxy Session Token field
    - Specify the URL `http://localhost:3000/mcp`
    - Click connect