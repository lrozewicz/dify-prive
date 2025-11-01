# Stop Generate

> Stops a generation task. Only supported in streaming mode.

## OpenAPI

````yaml en/openapi_completion.json post /completion-messages/{task_id}/stop
paths:
  path: /completion-messages/{task_id}/stop
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
        task_id:
          schema:
            - type: string
              required: true
              description: >-
                Task ID, can be obtained from the streaming chunk return of a
                `/completion-messages` request.
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
                      User identifier, used to define the identity of the
                      end-user, must be consistent with the user passed in the
                      send message interface.
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
          success:
            value:
              result: success
        description: Stop request successful.
  deprecated: false
  type: path
components:
  schemas: {}

````