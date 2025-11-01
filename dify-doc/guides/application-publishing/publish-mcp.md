# Publishing Dify Apps as MCP Servers

Dify now supports exposing your applications as [MCP](https://modelcontextprotocol.io/introduction) (Model Context Protocol) servers, enabling seamless integration with AI assistants like Claude Desktop and development environments like Cursor. This allows these tools to directly interact with your Dify apps as if they were native extensions.

<Note>
  If you're looking to use MCP tools within Dify workflows & agents, see [here](/en/guides/tools/mcp).
</Note>

## Configuring Your Dify App as an MCP Server

Navigate to your application's configuration interface in Dify, you'll find an MCP Server configuration module. The feature is disabled by default. When you toggle it on, Dify generates an unique MCP Server address for your application. This address serves as the connection point for external tools.

<Danger>
  Your MCP Server URL contains authentication credentials, so treat it like an API key. If you suspect it's been compromised, use the regenerate button to create a new URL. The old one will immediately stop working.
</Danger>

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=da15df02053b4df1ae8cd8d99f1acc01" alt="CleanShot 2025-07-07 at 08.18.02.png" title="CleanShot 2025-07-07 at 08.18.02.png" className="mx-auto" style={{ width:"46%" }} data-og-width="908" width="908" data-og-height="1988" height="1988" data-path="images/CleanShot2025-07-07at08.18.02.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=543a95cc551af0072c07713a9c819af9 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=18a082606921ed78ac449385f72c08b5 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=cfa0fa7e8a84c71393e8989902f786d4 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=4a0a81314232d4e139100e6ca32d4770 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=5b848b115dca8d84eb9cdfe9ca9f55f5 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/CleanShot2025-07-07at08.18.02.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=da97333283262b63bbeaa11aeb361c1a 2500w" />

## Integration with Claude Desktop

To connect your Dify app to Claude Desktop, you'll need to add a Claude integration. Go to your Claude Profile > Settings > Integrations > Add integration. Replace the Integration URL with your Dify app's Server URL.

## Integration with Cursor

For Cursor, create or edit the `.cursor/mcp.json` file in your project root:

```json  theme={"system"}
{
  "mcpServers": {
    "your-server-name": {
      "url": "your-server-url"
    }
  }
}
```

Simply replace the URL with your Dify app's MCP Server address. Cursor will automatically detect this configuration and make your Dify app available as a tool. You can add multiple Dify apps by including additional entries in the `mcpServers` object.

## Practical Considerations

* Descriptiveness

  When designing descriptions for your tool and its input parameters, think about how an AI would interpret them. Clear, specific descriptions lead to better invocations. Instead of "input data," specify "JSON object containing user profile with required fields: name, email, preferences."
* Latency

  The MCP protocol handles the communication layer, but your Dify app's performance still matters. If your app typically takes 30 seconds to process, that latency will be felt in the client application. Consider adding progress indicators or breaking complex workflows into smaller, faster operations.

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/en/guides/application-publishing/publish-mcp.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
