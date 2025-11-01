# Unbind Dataset and Knowledge Base Type Tag

> Unbinds a specific tag from a knowledge base.

## OpenAPI

````yaml en/openapi_knowledge.json post /datasets/tags/unbinding
paths:
  path: /datasets/tags/unbinding
  method: post
  servers:
    - url: '{apiBaseUrl}'
      description: The base URL for the Knowledge API.
      variables:
        apiBaseUrl:
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
      path: {}
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              target_id:
                allOf:
                  - type: string
                    description: The ID of the dataset.
                    format: uuid
              tag_id:
                allOf:
                  - type: string
                    description: The ID of the tag to unbind.
                    format: uuid
            required: true
            requiredProperties:
              - target_id
              - tag_id
        examples:
          example:
            value:
              target_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              tag_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
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