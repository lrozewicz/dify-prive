# Delete a Chunk in a Document

> Deletes a specific chunk (segment) from a document.

## OpenAPI

````yaml en/openapi_knowledge.json delete /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}
paths:
  path: /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}
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
              description: The ID of the document.
              format: uuid
        segment_id:
          schema:
            - type: string
              required: true
              description: The ID of the segment to delete.
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
            description: Successfully deleted the segment.
        examples: {}
        description: Successfully deleted the segment.
  deprecated: false
  type: path
components:
  schemas: {}

````