# Conversation Rename

> Rename the session.

## OpenAPI

````yaml en/openapi_chatflow.json post /conversations/{conversation_id}/name
paths:
  path: /conversations/{conversation_id}/name
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
              name:
                allOf:
                  - type: string
                    nullable: true
              auto_generate:
                allOf:
                  - type: boolean
                    default: false
              user:
                allOf:
                  - type: string
            required: true
            refIdentifier: '#/components/schemas/ConversationRenameRequest'
            requiredProperties:
              - user
        examples:
          example:
            value:
              name: <string>
              auto_generate: false
              user: <string>
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              id:
                allOf:
                  - type: string
                    format: uuid
              name:
                allOf:
                  - type: string
              inputs:
                allOf:
                  - type: object
                    additionalProperties: true
              status:
                allOf:
                  - type: string
              introduction:
                allOf:
                  - type: string
                    nullable: true
              created_at:
                allOf:
                  - type: integer
                    format: int64
              updated_at:
                allOf:
                  - type: integer
                    format: int64
            refIdentifier: '#/components/schemas/ConversationRenameResponse'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              name: <string>
              inputs: {}
              status: <string>
              introduction: <string>
              created_at: 123
              updated_at: 123
        description: Conversation renamed successfully.
  deprecated: false
  type: path
components:
  schemas: {}

````