# Get Conversation Variables

> Retrieve variables from a specific conversation.

## OpenAPI

````yaml en/openapi_chatflow.json get /conversations/{conversation_id}/variables
paths:
  path: /conversations/{conversation_id}/variables
  method: get
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
        last_id:
          schema:
            - type: string
              description: ID of the last record for pagination.
        limit:
          schema:
            - type: integer
              description: Number of items per page (Default 20, Max 100).
              maximum: 100
              minimum: 1
              default: 20
        variable_name:
          schema:
            - type: string
              description: Filter by variable name.
      header: {}
      cookie: {}
    body: {}
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              limit:
                allOf:
                  - type: integer
              has_more:
                allOf:
                  - type: boolean
              data:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/ConversationVariableItem'
            refIdentifier: '#/components/schemas/ConversationVariablesResponse'
        examples:
          example:
            value:
              limit: 123
              has_more: true
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  name: <string>
                  value_type: <string>
                  value: <string>
                  description: <string>
                  created_at: 123
                  updated_at: 123
        description: Successfully retrieved conversation variables.
    '404':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - type: integer
                    nullable: true
              code:
                allOf:
                  - type: string
                    nullable: true
              message:
                allOf:
                  - type: string
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Conversation not found.
  deprecated: false
  type: path
components:
  schemas:
    ConversationVariableItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        value_type:
          type: string
        value:
          type: string
        description:
          type: string
          nullable: true
        created_at:
          type: integer
          format: int64
        updated_at:
          type: integer
          format: int64

````