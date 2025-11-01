# Get Conversations

> Retrieve the conversation list for the current user.

## OpenAPI

````yaml en/openapi_chatflow.json get /conversations
paths:
  path: /conversations
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
      path: {}
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
        sort_by:
          schema:
            - type: enum<string>
              enum:
                - created_at
                - '-created_at'
                - updated_at
                - '-updated_at'
              description: Sorting field (e.g., -updated_at).
              default: '-updated_at'
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
                      $ref: '#/components/schemas/ConversationListItem'
            refIdentifier: '#/components/schemas/ConversationsListResponse'
        examples:
          example:
            value:
              limit: 123
              has_more: true
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  name: <string>
                  inputs: {}
                  status: <string>
                  introduction: <string>
                  created_at: 123
                  updated_at: 123
        description: Successfully retrieved conversations list.
  deprecated: false
  type: path
components:
  schemas:
    ConversationListItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        inputs:
          type: object
          additionalProperties: true
        status:
          type: string
        introduction:
          type: string
          nullable: true
        created_at:
          type: integer
          format: int64
        updated_at:
          type: integer
          format: int64

````