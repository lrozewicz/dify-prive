# Get the Document List of a Knowledge Base

> Retrieves a paginated list of all documents within a specified knowledge base.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets/{dataset_id}/documents
paths:
  path: /datasets/{dataset_id}/documents
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
      query:
        keyword:
          schema:
            - type: string
              description: Keyword to search for in document names.
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
              minimum: 1
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
                      $ref: '#/components/schemas/Document'
              has_more:
                allOf:
                  - type: boolean
              limit:
                allOf:
                  - type: integer
              total:
                allOf:
                  - type: integer
              page:
                allOf:
                  - type: integer
            refIdentifier: '#/components/schemas/DocumentListResponse'
        examples:
          example:
            value:
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  position: 123
                  data_source_type: <string>
                  data_source_info: {}
                  dataset_process_rule_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  name: <string>
                  created_from: <string>
                  created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  created_at: 123
                  tokens: 123
                  indexing_status: <string>
                  error: <string>
                  enabled: true
                  disabled_at: 123
                  disabled_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  archived: true
                  display_status: <string>
                  word_count: 123
                  hit_count: 123
                  doc_form: <string>
              has_more: true
              limit: 123
              total: 123
              page: 123
        description: A paginated list of documents.
  deprecated: false
  type: path
components:
  schemas:
    Document:
      type: object
      properties:
        id:
          type: string
          format: uuid
        position:
          type: integer
        data_source_type:
          type: string
        data_source_info:
          type: object
          nullable: true
        dataset_process_rule_id:
          type: string
          format: uuid
          nullable: true
        name:
          type: string
        created_from:
          type: string
        created_by:
          type: string
          format: uuid
        created_at:
          type: integer
          format: int64
        tokens:
          type: integer
        indexing_status:
          type: string
        error:
          type: string
          nullable: true
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
        archived:
          type: boolean
        display_status:
          type: string
        word_count:
          type: integer
        hit_count:
          type: integer
        doc_form:
          type: string

````