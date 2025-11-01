# Update Knowledge Base

> Updates the settings of a specific knowledge base.

## OpenAPI

````yaml en/openapi_knowledge.json patch /datasets/{dataset_id}
paths:
  path: /datasets/{dataset_id}
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
              description: The unique identifier of the knowledge base.
              format: uuid
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
                    description: New name for the knowledge base.
              description:
                allOf:
                  - type: string
                    description: New description for the knowledge base.
              indexing_technique:
                allOf:
                  - type: string
                    enum:
                      - high_quality
                      - economy
              permission:
                allOf:
                  - type: string
                    enum:
                      - only_me
                      - all_team_members
                      - partial_members
              embedding_model_provider:
                allOf:
                  - type: string
              embedding_model:
                allOf:
                  - type: string
              retrieval_model:
                allOf:
                  - $ref: '#/components/schemas/RetrievalModel'
              partial_member_list:
                allOf:
                  - type: array
                    description: List of member IDs for 'partial_members' permission.
                    items:
                      type: string
            required: true
            refIdentifier: '#/components/schemas/UpdateDatasetRequest'
        examples:
          example:
            value:
              name: <string>
              description: <string>
              indexing_technique: high_quality
              permission: only_me
              embedding_model_provider: <string>
              embedding_model: <string>
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
              partial_member_list:
                - <string>
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
              retrieval_model_dict:
                allOf:
                  - $ref: '#/components/schemas/RetrievalModel'
              tags:
                allOf:
                  - type: array
                    items:
                      type: object
              doc_form:
                allOf:
                  - type: string
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
              retrieval_model_dict:
                search_method: hybrid_search
                reranking_enable: true
                reranking_mode:
                  reranking_provider_name: <string>
                  reranking_model_name: <string>
                top_k: 123
                score_threshold_enabled: true
                score_threshold: 123
                weights: 123
              tags:
                - {}
              doc_form: <string>
        description: Successfully updated dataset details.
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