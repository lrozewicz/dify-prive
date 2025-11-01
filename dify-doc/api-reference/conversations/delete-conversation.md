# Delete Conversation

> Delete a conversation.

## OpenAPI

````yaml en/openapi_chatflow.json delete /conversations/{conversation_id}
paths:
  path: /conversations/{conversation_id}
  method: delete
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Advanced Chat App API. Replace {api_base_url} with
        the actual API base URL provided for your application (e.g., from
        props.appDetail.api_base_url).
      variables:
        api_base_url:
          type: string
          description: Actual base URL of the API
          default: https://api.dify.ai/v1
  request:
    security:
      - title: ApiKeyAuth
        parameters:
          query: {}
          header:
            Authorization:
              type: http
              scheme: bearer
              description: API Key authentication.
          cookie: {}
    parameters:
      path:
        conversation_id:
          schema:
            - type: string
              required: true
              description: Conversation ID.
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              user:
                allOf:
                  - type: string
                    description: >-
                      The user identifier. **Note**: The Service API does not
                      share conversations created by the WebApp. Conversations
                      created through the API are isolated from those created in
                      the WebApp interface.
            required: true
            requiredProperties:
              - user
        examples:
          example:
            value:
              user: <string>
  response:
    '204':
      _mintlify/placeholder:
        schemaArray:
          - type: any
            description: Conversation deleted successfully. No Content.
        examples: {}
        description: Conversation deleted successfully. No Content.
  deprecated: false
  type: path
components:
  schemas: {}

````