# Stop Chat Message Generation

> Stops a chat message generation task. Only supported in streaming mode.

## OpenAPI

````yaml en/openapi_chat.json post /chat-messages/{task_id}/stop
paths:
  path: /chat-messages/{task_id}/stop
  method: post
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Chat App API. Replace {api_base_url} with the
        actual API base URL provided for your application (e.g., from
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
              description: >-
                API Key authentication. For all API requests, include your API
                Key in the `Authorization` HTTP Header, prefixed with 'Bearer '.
                Example: `Authorization: Bearer {API_KEY}`. **Strongly recommend
                storing your API Key on the server-side, not shared or stored on
                the client-side, to avoid possible API-Key leakage that can lead
                to serious consequences.**
          cookie: {}
    parameters:
      path:
        task_id:
          schema:
            - type: string
              required: true
              description: >-
                Task ID, can be obtained from the streaming chunk return of a
                `/chat-messages` request.
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
                      User identifier, must be consistent with the user passed
                      in the send message interface. **Note**: The Service API
                      does not share conversations created by the WebApp.
                      Conversations created through the API are isolated from
                      those created in the WebApp interface.
            required: true
            requiredProperties:
              - user
        examples:
          example:
            value:
              user: abc-123
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              result:
                allOf:
                  - type: string
                    example: success
        examples:
          example:
            value:
              result: success
        description: Operation successful.
  deprecated: false
  type: path
components:
  schemas: {}

````