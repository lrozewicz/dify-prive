# Get Knowledge Base Type Tags

> Retrieves a list of all available knowledge base tags.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets/tags
paths:
  path: /datasets/tags
  method: get
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
    body: {}
  response:
    '200':
      application/json:
        schemaArray:
          - type: array
            items:
              allOf:
                - $ref: '#/components/schemas/Tag'
        examples:
          example:
            value:
              - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                name: <string>
                type: knowledge
                binding_count: 123
        description: A list of tags.
  deprecated: false
  type: path
components:
  schemas:
    Tag:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        type:
          type: string
          example: knowledge
        binding_count:
          type: integer

````