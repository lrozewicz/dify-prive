# Create an Empty Knowledge Base

> Creates a new, empty knowledge base (dataset) with specified configurations.

## OpenAPI

````yaml en/openapi_knowledge.json post /datasets
paths:
  path: /datasets
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
              name:
                allOf:
                  - type: string
                    description: Name of the knowledge base.
              description:
                allOf:
                  - type: string
                    description: Description of the knowledge base (optional).
              indexing_technique:
                allOf:
                  - type: string
                    description: The indexing technique to use.
                    enum:
                      - high_quality
                      - economy
              permission:
                allOf:
                  - type: string
                    description: Access permissions for the knowledge base.
                    enum:
                      - only_me
                      - all_team_members
                      - partial_members
              provider:
                allOf:
                  - type: string
                    description: The provider of the knowledge base.
                    enum:
                      - vendor
                      - external
              external_knowledge_api_id:
                allOf:
                  - type: string
                    description: >-
                      ID of the external knowledge API (if provider is
                      'external').
              external_knowledge_id:
                allOf:
                  - type: string
                    description: ID of the external knowledge (if provider is 'external').
              embedding_model:
                allOf:
                  - type: string
                    description: Name of the embedding model.
              embedding_model_provider:
                allOf:
                  - type: string
                    description: Provider of the embedding model.
              retrieval_model:
                allOf:
                  - $ref: '#/components/schemas/RetrievalModel'
            required: true
            refIdentifier: '#/components/schemas/CreateDatasetRequest'
            requiredProperties:
              - name
        examples:
          example:
            value:
              name: <string>
              description: <string>
              indexing_technique: high_quality
              permission: only_me
              provider: vendor
              external_knowledge_api_id: <string>
              external_knowledge_id: <string>
              embedding_model: <string>
              embedding_model_provider: <string>
              retrieval_model:
                search_method: hybrid_search
                reranking_enable: true
                reranking_mode:
                  reranking_provider_name: <string>
                  reranking_model_name: <string>
                top_k: 123
                score_threshold_enabled: true
                score_threshold: 123
                weights: 123
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              id:
                allOf:
                  - type: string
                    format: uuid
              name:
                allOf:
                  - type: string
              description:
                allOf:
                  - type: string
                    nullable: true
              provider:
                allOf:
                  - type: string
              permission:
                allOf:
                  - type: string
              data_source_type:
                allOf:
                  - type: string
                    nullable: true
              indexing_technique:
                allOf:
                  - type: string
                    nullable: true
              app_count:
                allOf:
                  - type: integer
              document_count:
                allOf:
                  - type: integer
              word_count:
                allOf:
                  - type: integer
              created_by:
                allOf:
                  - type: string
                    format: uuid
              created_at:
                allOf:
                  - type: integer
                    format: int64
              updated_by:
                allOf:
                  - type: string
                    format: uuid
              updated_at:
                allOf:
                  - type: integer
                    format: int64
              embedding_model:
                allOf:
                  - type: string
                    nullable: true
              embedding_model_provider:
                allOf:
                  - type: string
                    nullable: true
              embedding_available:
                allOf:
                  - type: boolean
                    nullable: true
            refIdentifier: '#/components/schemas/Dataset'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
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
        description: Successfully created dataset.
    '409':
      application/json:
        schemaArray:
          - type: object
            properties:
              code:
                allOf:
                  - type: string
                    description: A machine-readable error code.
              message:
                allOf:
                  - type: string
                    description: A human-readable error message.
              status:
                allOf:
                  - type: integer
                    description: The HTTP status code.
            refIdentifier: '#/components/schemas/ErrorResponse'
            example:
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        examples:
          example:
            value:
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        description: The dataset name already exists.
  deprecated: false
  type: path
components:
  schemas:
    RetrievalModel:
      type: object
      properties:
        search_method:
          type: string
          description: The search method to use for retrieval.
          enum:
            - hybrid_search
            - semantic_search
            - full_text_search
            - keyword_search
        reranking_enable:
          type: boolean
          description: Whether to enable a reranking model to improve search results.
        reranking_mode:
          type: object
          description: Configuration for the reranking model.
          properties:
            reranking_provider_name:
              type: string
              description: The provider of the rerank model.
            reranking_model_name:
              type: string
              description: The name of the rerank model.
          nullable: true
        top_k:
          type: integer
          description: The number of top matching results to return.
        score_threshold_enabled:
          type: boolean
          description: Whether to apply a score threshold to filter results.
        score_threshold:
          type: number
          format: float
          description: The minimum score for a result to be included.
          nullable: true
        weights:
          type: number
          format: float
          description: The weight of semantic search in a hybrid search mode.
          nullable: true

````