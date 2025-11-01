# Using MCP Tools

Use [tools](https://modelcontextprotocol.io/docs/concepts/tools) provided by external [MCP](https://modelcontextprotocol.io/introduction) servers directly in your Dify agents and workflow applications. Instead of being limited to existing Dify plugins, you can tap into a growing [ecosystem](https://mcpservers.org/) of MCP servers that provide specialized capabilities.

<Note>
  This article shows how to use MCP tools within Dify. If you're looking to publish an Dify application as an MCP server, check [here](/en/guides/application-publishing/publish-mcp).
</Note>

<Info>
  Currently, only MCP servers supporting [HTTP transport](https://modelcontextprotocol.io/docs/concepts/architecture#transport-layer) can be used.
</Info>

## Accessing MCP Server Management

Navigate to **Tools** → **MCP** in your Dify workspace. This is where you manage all external MCP servers that provide tools for your applications.

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=65d4b39cec4a998480db2c8a1ed36831" alt="6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png" data-og-width="3048" width="3048" data-og-height="1988" height="1988" data-path="images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c4e07c417db39bb1395a1d2fadf9a9d9 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=09fd00750e22ed7432355566f940e221 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=80399f660ddafb8c708852e425371cdf 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c76a6d0a048245f829ef2301dc7ba2d3 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f8d8795253a00d951ddb014217303b59 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/6cef1436fcc13a65ccedb54bcf5ab77eb87b8faba1098a85951839fb1907f2d2.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=3451f1d020257b2b0a8f69bbdcf06367 2500w" />

## Adding an MCP Server

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=dca573eca5488cc2b52f6e30eefb8dac" alt="b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png" title="b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png" className="mr-auto" style={{ width:"70%" }} data-og-width="1120" width="1120" data-og-height="912" height="912" data-path="images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=e18bc7b127110017510fe6fbc5ed4d7a 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=ba0d265c7f17ce0748b1e9e4bf5cdb63 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=e8e83a6949bca0dc8bbd0a0178eae9f7 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=1a66251fe235f30d38ca6d096aab4183 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f1a51f0f741191d9e797d2b5103e9500 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b5429131836c1caae84f4ce8b3b806221e39636723644961ce2f2a97d5421f16.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=9059fc725354528ae78cd91a8ea0a83b 2500w" />

Click **Add MCP Server (HTTP)** to connect a new external tool provider:

**Server URL**: The HTTP endpoint of the MCP server (e.g., `https://api.notion.com/mcp` for a Notion integration).

**Name & Icon**: Give it a name that describes what tools it provides. Dify auto-fetches icons when ever it can from the server domain, or you can choose your own.

**Server Identifier**: A unique ID (lowercase, numbers, underscores, hyphens, max 24 characters) that Dify uses to track this server.

<Warning>
  The server ID is permanent by design. If you change it, any existing agents or workflows using tools from this server will break. This is critical for [application portability](##application-portability).
</Warning>

## Authorization and Tool Discovery

After adding a server, Dify automatically:

1. **Discovers Available Tools**: Checks what capabilities the server provides
2. **Handles Authorization**: Initiates OAuth flows if the server requires authentication
3. **Fetches Tool Definitions**: Downloads tool schemas so they can be used in your applications
4. **Updates Tool Inventory**: Makes the tools available in agent and workflow builders

A server card is added once Dify successfully retrieves at least one usable tool:

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=ff64850c089ed5b06b64449f681f5e69" alt="fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png" data-og-width="1564" width="1564" data-og-height="550" height="550" data-path="images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=8ed17f21e927815caccfce7930a3c6ca 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=a328ab185ba46e5b525c3189f0222046 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=69a5c6a0a8e6768a2f95a670a6f1a750 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=647cc1d4d01f4444ad9b724ec27ad6fd 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=aa1abe04aaf40e5bcc091bec2e5dbe3f 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/fcef5ecad1deca82a1d8988c4bcb7cec745a0cd47945ff05fca588502cfaafbc.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=994777c21307bd1d0783461808748504 2500w" />

## Managing Connected Servers

Click any server card to:

**Update Tools**: Refresh available tools from the server. Use this when the external service adds new capabilities.

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=79785739094935dd3e0fd18c3975de33" alt="7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png" title="7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png" className="mx-auto" style={{ width:"59%" }} data-og-width="916" width="916" data-og-height="942" height="942" data-path="images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=948b3f759caf90942c2dd0e7085060ba 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c6409bdcf5890a4c54ea4d6da5267500 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d9b0f4c03d05c5ad5ab5fb102deb3b74 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=711306e1acfe802c28b14518614e977d 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=154b69d2ee313380d7da24b2ac61c574 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/7b526a64ff34b10a357511b2cd3e42f251a6786210eac71c58ca7bfccdf63f0c.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=34870307be56e14c4d808d7deebf1434 2500w" />

**Re-authorize**: Click on the authorization status to renew permissions.

**Edit Configuration**: Change server details.

<Warning>
  Note: URL changes trigger re-authorization, server ID changes break existing applications.
</Warning>

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=24748102cefe6d7c3886b5f7ae9af47b" alt="CleanShot 2025-07-07 at 07.28.04@2x.png" title="CleanShot 2025-07-07 at 07.28.04@2x.png" className="mx-auto" style={{ width:"60%" }} data-og-width="912" width="912" data-og-height="320" height="320" data-path="images/CleanShot2025-07-07at07.28.04@2x.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=58854ad72a20befeb1ba1270dc516f63 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=a1314847f3388732de2c8187eadeba8d 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=fb79249c422f275c88fb22ed7059782a 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=00fe62655d16498f13a950cb05582798 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c6f5022a45b82d93ce737f6621de5f1c 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.28.04@2x.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=6a017546f3ccbe72020f5be893fb54bb 2500w" />

**Remove Server**: Disconnects the server. Applications using its tools will show errors until you reconnect or remove those tools.

## Using MCP Tools in Your Applications

Once a server is configured, its tools appear in the tool selection interface when building:

### Agent Applications

* MCP tools appear alongside built-in tools in the agent configuration
* Tools are organized by server: "Notion MCP » Create Page", "Linear MCP » Create Issue"
* "Add All" option lets you quickly enable all tools from a server

### Workflow Applications

* MCP tools appear as available node types when building workflows
* Each tool node shows which server it comes from (helpful for troubleshooting)
* Complex tool parameters get JSON input interfaces for structured data

### Agent Nodes in Workflows

* MCP tools can be selected within agent nodes, just like in standalone agents

## Customizing MCP Tools for Your Use Case

When you add an MCP tool to an agent node or agent, you can customize how it behaves:

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=73042add2d9b4ec78771b1fd7fc7e899" alt="CleanShot 2025-07-07 at 07.41.33@2x.png" title="CleanShot 2025-07-07 at 07.41.33@2x.png" className="mx-auto" style={{ width:"57%" }} data-og-width="798" width="798" data-og-height="1020" height="1020" data-path="images/CleanShot2025-07-07at07.41.33@2x.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=51613a1444ee56105a0690ac02106e29 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=a9c030ff90b3840bf3231eb9cc861f1e 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=c82ed7dca34de0e5c313e5f87f57267c 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=be583e212d1f5bee5cb4740e9dd6c16c 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=6285419c8411318e8bffae19770357ac 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at07.41.33@2x.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=a4f96f8b9422ee5b5432fb3b867f0d6a 2500w" />

### Tool Description

You can override the default description that comes from the MCP server. This is useful for making the description more specific to your use case.

### Parameter Configuration (Reasoning Config)

For each tool parameter, you can choose between:

**Auto**: Let the AI model determine the parameter value based on context (default behavior)

**Fixed Value**: Set a specific value (can be a static value or a variable) that will always be used, removing the parameter from AI inference

This is powerful for:

* Setting consistent configuration values (like `numResults: 10` for search tools)
* Pre-filling parameters that shouldn't change (like specific API endpoints or format preferences)
* Simplifying tool usage by reducing the number of parameters the AI needs to handle

For example, with a web search tool, you might:

* Keep `query` on "Auto" so the AI determines what to search for
* Set `numResults` to a fixed value like "5" to limit response size
* Set other parameters like search filters to fixed values for consistent behavior

## Application Portability

When you export Dify applications that use MCP tools:

**DSL Export**: The exported DSL includes references to MCP servers by their IDs.

**Environment Migration**: To use the application elsewhere, add the same MCP servers with identical IDs in the target environment.

**Sharing Applications**: Document which MCP servers your application depends on, including URLs and required server IDs.

## Troubleshooting Integration Issues

**"Unconfigured Server"**: Authorization failed or no tools found. Check server URL and re-authorize.

**Missing Tools in Applications**: Hit "Update Tools" - the external service may have changed its offerings.

**Broken Applications After Server Changes**: If you modified server IDs or removed servers, applications will show tool errors. Re-add servers with original IDs to restore functionality.

## Best Practices

**Consistent Server IDs**: Use descriptive, permanent IDs like `github-mcp` or `salesforce-api`. Never change them once applications depend on them.

**Environment Consistency**: Keep the same MCP server configurations across development, staging, and production environments.

**Tool Customization**: Take advantage of parameter configuration to make tools behave consistently in your applications. Set fixed values for configuration parameters and let the AI handle dynamic inputs.

**Tool Documentation**: Document which external tools your applications use, what customizations you've made, and what they do. This helps team members understand application dependencies.

**Gradual Updates**: When external services update their MCP servers, test tool changes in development before updating production integrations.

**Backup Plans**: Consider how your applications will behave if an external MCP server becomes unavailable.

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/tools/mcp.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
