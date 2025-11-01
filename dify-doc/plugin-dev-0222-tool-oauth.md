# Add OAuth Support to Your Tool Plugin

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=b3d8e10da9e99d6b184a19681a24795f" alt="b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png" data-og-width="1280" width="1280" data-og-height="622" height="622" data-path="images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=1b81412bc0e684b946848da8ef8d5d1d 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=0bdc7f1dc729db30e2ac054248310917 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=9951e9e3302700347f52d14f9afc8995 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=31e22494aa06b8e5b0bea55316602e06 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=461fe04cca7081ee9f53b46c56c8813b 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/b0e673ba3e339b31ac36dc3cd004df04787bcaa64bb6d2cac6feb7152b7b515f.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f978c0902bebc508376f37cb32552a17 2500w" />

This guide teaches you how to build [OAuth](https://oauth.net/2/) support into your tool plugin.

OAuth is a better way to authorize tool plugins that need to access user data from third-party services, like Gmail or GitHub. Instead of requiring the user to manually enter API keys, OAuth lets the tool act on behalf of the user with their explicit consent.

## Background

OAuth in Dify involves **two separate flows** that developers should understand and design for.

### Flow 1: OAuth Client Setup (Admin / Developer Flow)

<Note>
  On Dify Cloud, Dify team would create OAuth apps for popular tool plugins and set up OAuth clients, saving users the trouble to configure this themselves.

  Admins of Self-Hosted Dify instances must go through this setup flow.
</Note>

Dify instance's admins or developers first need to register an OAuth app at the third-party service as a trusted application. From this, they'll be able to obtain the necessary credentials to configure the Dify tool provider as an OAuth client.

As an example, here are the steps to setting up an OAuth client for Dify's Gmail tool provider:

<AccordionGroup>
  <Accordion title="Create a Google Cloud Project">
    1. Go to [Google Cloud Console](https://console.cloud.google.com) and create a new project, or select existing one
    2. Enable the required APIs (e.g., Gmail API)
  </Accordion>

  <Accordion title="Configure OAuth Consent Screen:">
    1. Navigate to **APIs & Services** > **OAuth consent screen**
    2. Choose **External** user type for public plugins
    3. Fill in application name, user support email, and developer contact
    4. Add authorized domains if needed
    5. For testing: Add test users in the **Test users** section
  </Accordion>

  <Accordion title="Create OAuth 2.0 Credentials">
    1. Go to **APIs & Services** > **Credentials**
    2. Click **Create Credentials** > **OAuth 2.0 Client IDs**
    3. Choose **Web application** type
    4. A`client_id` and a`client_secret` will be generated. Save these as the credentials.
  </Accordion>

  <Accordion title="Enter Credentials in Dify">
    Enter the client\_id and client\_secret on the OAuth Client configuration popup to set up the tool provider as a client.

    <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=74c708fcb3f94b14ae88bd9cb2ddfafc" alt="acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png" title="acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png" className="mx-auto" style={{ width:"66%" }} data-og-width="960" width="960" data-og-height="810" height="810" data-path="images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d9b20ce70f508b467341ffe782458f0a 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=185b6f0c61294661c8730bcadc862ac8 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=09732ba32cd58288d4c44132ea196998 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=e0ae536e140a851080a0e78ca7026d1b 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=01c8eabe9a333498b8190ea267723e38 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/acd5f5057235c3a0c554abaedcf276fb48f80567f0231eae9158a795f8e1c45d.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=3f2c6147764a539aafba462198eb9db7 2500w" />
  </Accordion>

  <Accordion title="Authorize Redirect URI">
    Register the redirect URI generated by Dify on the Google OAuth Client's page:

    <img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=5dd5e64c3578082e079cc257b583dc92" alt="dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png" title="dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png" className="mx-auto" style={{ width:"77%" }} data-og-width="1050" width="1050" data-og-height="676" height="676" data-path="images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d4fe906c35edd8502f42cb6e5ee5cd22 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=82255be0b9e2e4bf023c01dc8dca1e9e 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=93c66b32acfac66200b5af197ae2b92b 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=fac7c5068a984b48bb946386a87e1c5e 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f754c1f202e3702f6f6cc6d2d6c4e917 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/dfe60a714a275c5bf65f814673bd2f0a0db4fda27573a2f0b28a1c39e4c61da2.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=102539b9830274c0463536b8fa90dc37 2500w" />

    <Info>
      Dify displays the `redirect_uri`  in the OAuth Client configuration popup. It usually follows the format:

      ```bash  theme={"system"}
      https://{your-dify-domain}/console/api/oauth/plugin/{plugin-id}/{provider-name}/{tool-name}/callback
      ```

      For self-hosted Dify, the `your-dify-domain` should be consistent with the `CONSOLE_WEB_URL`.
    </Info>
  </Accordion>
</AccordionGroup>

<Tip>
  Each service has unique requirements, so always consult the specific OAuth documentation for the services you're integrating with.
</Tip>

### Flow 2: User Authorization (Dify User Flow)

After configuring OAuth clients, individual Dify users can now authorize your plugin to access their personal accounts.

<img src="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=9a02c9e14158c9cb553efe0140e78519" alt="833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png" title="833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png" className="mx-auto" style={{ width:"67%" }} data-og-width="816" width="816" data-og-height="510" height="510" data-path="images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png" data-optimize="true" data-opv="3" srcset="https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=280&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=8189369f1b656f551c6e0bb37b1a86ba 280w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=560&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=d6f44262beb7ddfbf113990bd941dab4 560w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=840&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=f803d2cee828e43dd783d31101b68c04 840w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=1100&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=de8e7740f20743f21acc267d5a1fdfee 1100w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=1650&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=fd9cd566c47f548c224f522cce12e041 1650w, https://mintcdn.com/dify-6c0370d8/7ofzWAXbPyxqXN2g/images/833c205f5441910763b27d3e3ff0c4449a730a690da91abc3ce032c70da04223.png?w=2500&fit=max&auto=format&n=7ofzWAXbPyxqXN2g&q=85&s=faa5dd33f041480ca80d804e94df2368 2500w" />

## Implementation

### 1. Define OAuth Schema in Provider Manifest

The `oauth_schema` section of the provider manifest definitions tells Dify what credentials your plugin OAuth needs and what the OAuth flow will produce. Two schemas are required for setting up OAuth:

#### client\_schema

Defines the input for OAuth client setup:

```yaml gmail.yaml theme={"system"}
oauth_schema:
  client_schema:
    - name: "client_id"
      type: "secret-input"
      required: true
      url: "https://developers.google.com/identity/protocols/oauth2"
    - name: "client_secret"
      type: "secret-input" 
      required: true
```

<Info>
  The `url` field links directly to help documentations for the third-party service. This helps confused admins / developers.
</Info>

#### credentials\_schema

Specifies what the user authorization flow produces (Dify manages these automatically):

```yaml  theme={"system"}
# also under oauth_schema
  credentials_schema:
    - name: "access_token"
      type: "secret-input"
    - name: "refresh_token"
      type: "secret-input"
    - name: "expires_at"
      type: "secret-input"
```

<Info>
  Include both `oauth_schema` and `credentials_for_provider` to offer OAuth + API key auth options.
</Info>

### 2. Complete Required OAuth Methods in Tool Provider

Add these imports to where your `ToolProvider` is implemented:

```python  theme={"system"}
from dify_plugin.entities.oauth import ToolOAuthCredentials
from dify_plugin.errors.tool import ToolProviderCredentialValidationError, ToolProviderOAuthError
```

Your `ToolProvider` class must implement these three OAuth methods (taking `GmailProvider`  as an example):

<Warning>
  Under no circumstances should the `client_secret` be returned in the credentials of `ToolOAuthCredentials`, as this could lead to security issues.
</Warning>

<CodeGroup>
  ```python _oauth_get_authorization_url expandable theme={"system"}
  def _oauth_get_authorization_url(self, redirect_uri: str, system_credentials: Mapping[str, Any]) -> str:
  	"""
  	Generate the authorization URL using credentials from OAuth Client Setup Flow. 
      This URL is where users grant permissions.
      """
      # Generate random state for CSRF protection (recommended for all OAuth flows)
      state = secrets.token_urlsafe(16)
      
      # Define Gmail-specific scopes - request minimal necessary permissions
      scope = "read:user read:data"  # Replace with your required scopes
      
      # Assemble Gmail-specific payload
      params = {
          "client_id": system_credentials["client_id"],    # From OAuth Client Setup
          "redirect_uri": redirect_uri,                    # Dify generates this - DON'T modify
          "scope": scope,                                  
          "response_type": "code",                         # Standard OAuth authorization code flow
          "access_type": "offline",                        # Critical: gets refresh token (if supported)
          "prompt": "consent",                             # Forces reauth when scopes change (if supported)
          "state": state,                                  # CSRF protection
      }
      
      return f"{self._AUTH_URL}?{urllib.parse.urlencode(params)}"
  ```

  ```python _oauth_get_credentials expandable theme={"system"}
  def _oauth_get_credentials(
      self, redirect_uri: str, system_credentials: Mapping[str, Any], request: Request
  ) -> ToolOAuthCredentials:
      """
      Exchange authorization code for access token and refresh token. This is called
  	to creates ONE credential set for one account connection
      """
      # Extract authorization code from OAuth callback
      code = request.args.get("code")
      if not code:
          raise ToolProviderOAuthError("Authorization code not provided")
      
      # Check for authorization errors from OAuth provider
      error = request.args.get("error")
      if error:
          error_description = request.args.get("error_description", "")
          raise ToolProviderOAuthError(f"OAuth authorization failed: {error} - {error_description}")
      
      # Exchange authorization code for tokens using OAuth Client Setup credentials

  	# Assemble Gmail-specific payload
      data = {
          "client_id": system_credentials["client_id"],        # From OAuth Client Setup
          "client_secret": system_credentials["client_secret"], # From OAuth Client Setup
          "code": code,                                        # From user's authorization
          "grant_type": "authorization_code",                  # Standard OAuth flow type
          "redirect_uri": redirect_uri,                        # Must exactly match authorization URL
      }
      
      headers = {"Content-Type": "application/x-www-form-urlencoded"}
      
      try:
          response = requests.post(
              self._TOKEN_URL,
              data=data,
              headers=headers,
              timeout=10
          )
          response.raise_for_status()
          
          token_data = response.json()
          
          # Handle OAuth provider errors in response
          if "error" in token_data:
              error_desc = token_data.get('error_description', token_data['error'])
              raise ToolProviderOAuthError(f"Token exchange failed: {error_desc}")
          
          access_token = token_data.get("access_token")
          if not access_token:
              raise ToolProviderOAuthError("No access token received from provider")
          
          # Build credentials dict matching your credentials_schema
          credentials = {
              "access_token": access_token,
              "token_type": token_data.get("token_type", "Bearer"),
          }
          
          # Include refresh token if provided (critical for long-term access)
          refresh_token = token_data.get("refresh_token")
          if refresh_token:
              credentials["refresh_token"] = refresh_token
          
          # Handle token expiration - some providers don't provide expires_in
          expires_in = token_data.get("expires_in", 3600)  # Default to 1 hour
          expires_at = int(time.time()) + expires_in
          
          return ToolOAuthCredentials(credentials=credentials, expires_at=expires_at)
          
      except requests.RequestException as e:
          raise ToolProviderOAuthError(f"Network error during token exchange: {str(e)}")
      except Exception as e:
          raise ToolProviderOAuthError(f"Failed to exchange authorization code: {str(e)}")
  ```

  ```python _oauth_refresh_credentials theme={"system"}
  def _oauth_refresh_credentials(
      self, redirect_uri: str, system_credentials: Mapping[str, Any], credentials: Mapping[str, Any]
  ) -> ToolOAuthCredentials:
      """
      Refresh the credentials using refresh token. 
  	Dify calls this automatically when tokens expire
      """
      refresh_token = credentials.get("refresh_token")
      if not refresh_token:
          raise ToolProviderOAuthError("No refresh token available")

      # Standard OAuth refresh token flow
      data = {
          "client_id": system_credentials["client_id"],       # From OAuth Client Setup
          "client_secret": system_credentials["client_secret"], # From OAuth Client Setup
          "refresh_token": refresh_token,                     # From previous authorization
          "grant_type": "refresh_token",                      # OAuth refresh flow
      }

      headers = {"Content-Type": "application/x-www-form-urlencoded"}

      try:
          response = requests.post(
              self._TOKEN_URL,
              data=data,
              headers=headers,
              timeout=10
          )
          response.raise_for_status()

          token_data = response.json()

          # Handle refresh errors
          if "error" in token_data:
              error_desc = token_data.get('error_description', token_data['error'])
              raise ToolProviderOAuthError(f"Token refresh failed: {error_desc}")

          access_token = token_data.get("access_token")
          if not access_token:
              raise ToolProviderOAuthError("No access token received from provider")

          # Build new credentials, preserving existing refresh token
          new_credentials = {
              "access_token": access_token,
              "token_type": token_data.get("token_type", "Bearer"),
              "refresh_token": refresh_token,  # Keep existing refresh token
          }

          # Handle token expiration
          expires_in = token_data.get("expires_in", 3600)

          # update refresh token if new one provided
          new_refresh_token = token_data.get("refresh_token")
          if new_refresh_token:
              new_credentials["refresh_token"] = new_refresh_token

          # Calculate new expiration timestamp for Dify's token management
          expires_at = int(time.time()) + expires_in

          return ToolOAuthCredentials(credentials=new_credentials, expires_at=expires_at)

      except requests.RequestException as e:
          raise ToolProviderOAuthError(f"Network error during token refresh: {str(e)}")
      except Exception as e:
          raise ToolProviderOAuthError(f"Failed to refresh credentials: {str(e)}")
  ```
</CodeGroup>

### 3. Access Tokens in Your Tools

You may use OAuth credentials to make authenticated API calls in your `Tool` implementation like so:

```python  theme={"system"}
class YourTool(BuiltinTool):
    def _invoke(self, user_id: str, tool_parameters: dict[str, Any]) -> ToolInvokeMessage:
        if self.runtime.credential_type == CredentialType.OAUTH:
            access_token = self.runtime.credentials["access_token"]
        
        response = requests.get("https://api.service.com/data",
                              headers={"Authorization": f"Bearer {access_token}"})
        return self.create_text_message(response.text)
```

`self.runtime.credentials` automatically provides the current user's tokens. Dify handles refresh automatically.

For plugins that support both OAuth and API\_KEY authentication, you can use `self.runtime.credential_type` to differentiate between the two authentication types.

### 4. Specify the Correct Versions

Previous versions of the plugin SDK and Dify do not support OAuth authentication. Therefore, you need to set the plugin SDK version to:

```
dify_plugin>=0.4.2,<0.5.0.
```

In `manifest.yaml`, add the minimum Dify version:

```yaml  theme={"system"}
meta:
  version: 0.0.1
  arch:
    - amd64
    - arm64
  runner:
    language: python
    version: "3.12"
    entrypoint: main
  minimum_dify_version: 1.7.1
```

***

[Edit this page](https://github.com/langgenius/dify-docs/edit/main/plugin-dev-en/0222-tool-oauth.mdx) | [Report an issue](https://github.com/langgenius/dify-docs/issues/new?template=docs.yml)
