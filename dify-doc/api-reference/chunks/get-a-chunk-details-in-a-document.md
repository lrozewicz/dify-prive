# Get a Chunk Details in a Document

> Retrieves the details of a specific chunk (segment) within a document.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}
paths:
  path: /datasets/{dataset_id}/documents/{document_id}/segments/{segment_id}
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
              description: The ID of the segment.
              format: uuid
      query: {}
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
                  - $ref: '#/components/schemas/Segment'
              doc_form:
                allOf:
                  - type: string
            refIdentifier: '#/components/schemas/SegmentDetailResponse'
        examples:
          example:
            value:
              data:
                id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                position: 123
                document_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                content: <string>
                answer: <string>
                word_count: 123
                tokens: 123
                keywords:
                  - <string>
                index_node_id: <string>
                index_node_hash: <string>
                hit_count: 123
                enabled: true
                disabled_at: 123
                disabled_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                status: <string>
                created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                created_at: 123
                indexing_at: 123
                completed_at: 123
                error: <string>
                stopped_at: 123
              doc_form: <string>
        description: Detailed information about the segment.
  deprecated: false
  type: path
components:
  schemas:
    Segment:
      type: object
      properties:
        id:
          type: string
          format: uuid
        position:
          type: integer
        document_id:
          type: string
          format: uuid
        content:
          type: string
        answer:
          type: string
          nullable: true
        word_count:
          type: integer
        tokens:
          type: integer
        keywords:
          type: array
          items:
            type: string
        index_node_id:
          type: string
        index_node_hash:
          type: string
        hit_count:
          type: integer
        enabled:
          type: boolean
        disabled_at:
          type: integer
          format: int64
          nullable: true
        disabled_by:
          type: string
          format: uuid
          nullable: true
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