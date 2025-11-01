# Get Conversation History Messages

> Returns historical chat records in a scrolling load format.

## OpenAPI

````yaml en/openapi_chatflow.json get /messages
paths:
  path: /messages
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
        conversation_id:
          schema:
            - type: string
              required: true
              description: Conversation ID.
        user:
          schema:
            - type: string
              required: true
              description: >-
                User identifier. **Note**: The Service API does not share
                conversations created by the WebApp. Conversations created
                through the API are isolated from those created in the WebApp
                interface.
        first_id:
          schema:
            - type: string
              description: >-
                ID of the first chat record on the current page (for
                pagination).
        limit:
          schema:
            - type: integer
              description: Number of items per page.
              default: 20
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
                      $ref: '#/components/schemas/ConversationMessageItem'
            refIdentifier: '#/components/schemas/ConversationHistoryResponse'
        examples:
          example:
            value:
              limit: 123
              has_more: true
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  conversation_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  inputs: {}
                  query: <string>
                  answer: <string>
                  message_files:
                    - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                      type: <string>
                      url: <string>
                      belongs_to: user
                  feedback:
                    rating: like
                  retriever_resources:
                    - position: 123
                      dataset_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                      dataset_name: <string>
                      document_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                      document_name: <string>
                      segment_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                      score: 123
                      content: <string>
                  created_at: 123
        description: Successfully retrieved conversation history.
  deprecated: false
  type: path
components:
  schemas:
    RetrieverResource:
      type: object
      properties:
        position:
          type: integer
        dataset_id:
          type: string
          format: uuid
        dataset_name:
          type: string
        document_id:
          type: string
          format: uuid
        document_name:
          type: string
        segment_id:
          type: string
          format: uuid
        score:
          type: number
          format: float
        content:
          type: string
    ConversationMessageItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        conversation_id:
          type: string
          format: uuid
        inputs:
          type: object
          additionalProperties: true
        query:
          type: string
        answer:
          type: string
        message_files:
          type: array
          items:
            $ref: '#/components/schemas/MessageFileItem'
        feedback:
          type: object
          nullable: true
          properties:
            rating:
              type: string
              enum:
                - like
                - dislike
        retriever_resources:
          type: array
          items:
            $ref: '#/components/schemas/RetrieverResource'
        created_at:
          type: integer
          format: int64
    MessageFileItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        type:
          type: string
        url:
          type: string
          format: url
        belongs_to:
          type: string
          enum:
            - user
            - assistant

````