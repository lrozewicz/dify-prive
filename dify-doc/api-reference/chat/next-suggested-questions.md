# Next Suggested Questions

> Get next questions suggestions for the current message.

## OpenAPI

````yaml en/openapi_chat.json get /messages/{message_id}/suggested
paths:
  path: /messages/{message_id}/suggested
  method: get
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
        message_id:
          schema:
            - type: string
              required: true
              description: Message ID.
      query:
        user:
          schema:
            - type: string
              required: true
              description: >-
                User identifier. **Note**: The Service API does not share
                conversations created by the WebApp. Conversations created
                through the API are isolated from those created in the WebApp
                interface.
      header: {}
      cookie: {}
    body: {}
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
              data:
                allOf:
                  - type: array
                    items:
                      type: string
                    example:
                      - a
                      - b
                      - c
            refIdentifier: '#/components/schemas/SuggestedQuestionsResponse'
        examples:
          example:
            value:
              result: success
              data:
                - a
                - b
                - c
        description: Successfully retrieved suggested questions.
  deprecated: false
  type: path
components:
  schemas: {}

````