# Stop Advanced Chat Message Generation

> Stops an advanced chat message generation task. Only supported in streaming mode.

## OpenAPI

````yaml en/openapi_chatflow.json post /chat-messages/{task_id}/stop
paths:
  path: /chat-messages/{task_id}/stop
  method: post
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
        task_id:
          schema:
            - type: string
              required: true
              description: Task ID from the streaming chunk.
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
                      User identifier, consistent with the send message call.
                      **Note**: The Service API does not share conversations
                      created by the WebApp. Conversations created through the
                      API are isolated from those created in the WebApp
                      interface.
            required: true
            requiredProperties:
              - user
        examples:
          example:
            value:
              user: <string>
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