# Get Child Chunks

> Retrieves a list of child chunks for a specific parent segment.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}/child_chunks
paths:
  path: >-
    /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}/child_chunks
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
              description: The ID of the parent segment.
              format: uuid
      query:
        keyword:
          schema:
            - type: string
              description: Search keyword to filter child chunks.
        page:
          schema:
            - type: integer
              description: Page number for pagination.
              default: 1
        limit:
          schema:
            - type: integer
              description: Number of items to return per page.
              maximum: 100
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
              data:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/ChildChunk'
              total:
                allOf:
                  - type: integer
              total_pages:
                allOf:
                  - type: integer
              page:
                allOf:
                  - type: integer
              limit:
                allOf:
                  - type: integer
            refIdentifier: '#/components/schemas/ChildChunkListResponse'
        examples:
          example:
            value:
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  segment_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  content: <string>
                  word_count: 123
                  tokens: 123
                  index_node_id: <string>
                  index_node_hash: <string>
                  status: <string>
                  created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  created_at: 123
                  indexing_at: 123
                  completed_at: 123
                  error: <string>
                  stopped_at: 123
              total: 123
              total_pages: 123
              page: 123
              limit: 123
        description: A paginated list of child chunks.
  deprecated: false
  type: path
components:
  schemas:
    ChildChunk:
      type: object
      description: Represents a child chunk in a hierarchical segmentation.
      properties:
        id:
          type: string
          format: uuid
        segment_id:
          type: string
          format: uuid
        content:
          type: string
        word_count:
          type: integer
        tokens:
          type: integer
        index_node_id:
          type: string
        index_node_hash:
          type: string
        status:
          type: string
        created_by:
          type: string
          format: uuid
        created_at:
          type: integer
          format: int64
        indexing_at:
          type: integer
          format: int64
        completed_at:
          type: integer
          format: int64
        error:
          type: string
          nullable: true
        stopped_at:
          type: integer
          format: int64
          nullable: true

````