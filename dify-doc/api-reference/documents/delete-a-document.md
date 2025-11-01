# Delete a Document

> Deletes a specific document from a knowledge base.

## OpenAPI

````yaml en/openapi_knowledge.json delete /datasets/{dataset_id}/documents/{document_id}
paths:
  path: /datasets/{dataset_id}/documents/{document_id}
  method: delete
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
        document_id:
          schema:
            - type: string
              required: true
              description: The ID of the document to delete.
              format: uuid
      query: {}
      header: {}
      cookie: {}
    body: {}
  response:
    '204':
      _mintlify/placeholder:
        schemaArray:
          - type: any
            description: Successfully deleted the document.
        examples: {}
        description: Successfully deleted the document.
  deprecated: false
  type: path
components:
  schemas: {}

````