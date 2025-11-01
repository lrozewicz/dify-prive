# Get Knowledge Base List

> Retrieves a list of knowledge bases, with options for pagination and filtering.

## OpenAPI

````yaml en/openapi_knowledge.json get /datasets
paths:
  path: /datasets
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
      query:
        keyword:
          schema:
            - type: string
              description: Search keyword to filter datasets by name.
        tag_ids:
          schema:
            - type: array
              items:
                allOf:
                  - type: string
              description: >-
                List of tag IDs to filter by. Datasets must have all specified
                tags.
          style: form
          explode: false
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
        include_all:
          schema:
            - type: boolean
              description: >-
                Whether to include all datasets. This is effective only for
                workspace owners.
              default: false
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
                      $ref: '#/components/schemas/Dataset'
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
            refIdentifier: '#/components/schemas/DatasetListResponse'
        examples:
          example:
            value:
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  name: <string>
                  description: <string>
                  provider: <string>
                  permission: <string>
                  data_source_type: <string>
                  indexing_technique: <string>
                  app_count: 123
                  document_count: 123
                  word_count: 123
                  created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  created_at: 123
                  updated_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  updated_at: 123
                  embedding_model: <string>
                  embedding_model_provider: <string>
                  embedding_available: true
              has_more: true
              limit: 123
              total: 123
              page: 123
        description: A paginated list of datasets.
  deprecated: false
  type: path
components:
  schemas:
    Dataset:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        description:
          type: string
          nullable: true
        provider:
          type: string
        permission:
          type: string
        data_source_type:
          type: string
          nullable: true
        indexing_technique:
          type: string
          nullable: true
        app_count:
          type: integer
        document_count:
          type: integer
        word_count:
          type: integer
        created_by:
          type: string
          format: uuid
        created_at:
          type: integer
          format: int64
        updated_by:
          type: string
          format: uuid
        updated_at:
          type: integer
          format: int64
        embedding_model:
          type: string
          nullable: true
        embedding_model_provider:
          type: string
          nullable: true
        embedding_available:
          type: boolean
          nullable: true

````