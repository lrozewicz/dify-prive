# Get Document Embedding Status (Progress)

> Retrieves the indexing status for a batch of documents, showing the progress of embedding and processing.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets/{dataset_id}/documents/{batch}/indexing-status
paths:
  path: /datasets/{dataset_id}/documents/{batch}/indexing-status
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
        batch:
          schema:
            - type: string
              required: true
              description: The batch number returned from the document creation endpoint.
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
                  - type: array
                    items:
                      $ref: '#/components/schemas/IndexingStatus'
        examples:
          example:
            value:
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  indexing_status: <string>
                  processing_started_at: 123
                  parsing_completed_at: 123
                  cleaning_completed_at: 123
                  splitting_completed_at: 123
                  completed_at: 123
                  paused_at: 123
                  error: <string>
                  stopped_at: 123
                  completed_segments: 123
                  total_segments: 123
        description: Indexing status of the documents in the batch.
  deprecated: false
  type: path
components:
  schemas:
    IndexingStatus:
      type: object
      properties:
        id:
          type: string
          format: uuid
        indexing_status:
          type: string
        processing_started_at:
          type: number
          format: float
        parsing_completed_at:
          type: number
          format: float
        cleaning_completed_at:
          type: number
          format: float
        splitting_completed_at:
          type: number
          format: float
        completed_at:
          type: number
          format: float
          nullable: true
        paused_at:
          type: number
          format: float
          nullable: true
        error:
          type: string
          nullable: true
        stopped_at:
          type: number
          format: float
          nullable: true
        completed_segments:
          type: integer
        total_segments:
          type: integer

````