# Message Feedback

> End-users can provide feedback messages, facilitating application developers to optimize expected outputs.

## OpenAPI

````yaml en/openapi_completion.json post /messages/{message_id}/feedbacks
paths:
  path: /messages/{message_id}/feedbacks
  method: post
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Completion App API. Replace {api_base_url} with the
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
              description: Message ID for which feedback is being provided.
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              rating:
                allOf:
                  - type: string
                    enum:
                      - like
                      - dislike
                      - null
                    nullable: true
                    description: >-
                      Upvote as `like`, downvote as `dislike`, revoke
                      upvote/downvote as `null`.
              user:
                allOf:
                  - type: string
                    description: >-
                      User identifier, defined by the developer's rules, must be
                      unique within the application.
              content:
                allOf:
                  - type: string
                    description: The specific content of message feedback.
            required: true
            refIdentifier: '#/components/schemas/MessageFeedbackRequest'
            requiredProperties:
              - user
        examples:
          like_example:
            value:
              rating: like
              user: abc-123
              content: message feedback information
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
          success:
            value:
              result: success
        description: Feedback submitted successfully.
  deprecated: false
  type: path
components:
  schemas: {}

````