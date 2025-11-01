# Update Document Status

> Performs a batch action to update the status of one or more documents (e.g., enable, disable, archive).

## OpenAPI

````yaml en/openapi_knowledge.json patch /datasets/{dataset_id}/documents/status/{action}
paths:
  path: /datasets/{dataset_id}/documents/status/{action}
  method: patch
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
      path:
        dataset_id:
          schema:
            - type: string
              required: true
              description: The ID of the knowledge base.
              format: uuid
        action:
          schema:
            - type: enum<string>
              enum:
                - enable
                - disable
                - archive
                - un_archive
              required: true
              description: The action to perform on the documents.
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              document_ids:
                allOf:
                  - type: array
                    description: A list of document IDs to perform the action on.
                    items:
                      type: string
                      format: uuid
            required: true
            requiredProperties:
              - document_ids
        examples:
          example:
            value:
              document_ids:
                - 3c90c3cc-0d44-4b50-8888-8dd25736052a
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