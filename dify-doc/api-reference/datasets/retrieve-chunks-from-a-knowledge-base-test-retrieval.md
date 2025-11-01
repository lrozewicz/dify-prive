# Retrieve Chunks from a Knowledge Base / Test Retrieval

> Performs a search query against a knowledge base to retrieve the most relevant chunks (segments). This endpoint can be used for both production retrieval and test retrieval.

## OpenAPI

````yaml en/openapi_knowledge.json post /datasets/{dataset_id}/retrieve
paths:
  path: /datasets/{dataset_id}/retrieve
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
      path:
        dataset_id:
          schema:
            - type: string
              required: true
              description: The ID of the knowledge base to retrieve from.
              format: uuid
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              query:
                allOf:
                  - type: string
                    description: The search query string.
              retrieval_model:
                allOf:
                  - allOf:
                      - $ref: '#/components/schemas/RetrievalModel'
                      - type: object
                        properties:
                          metadata_filtering_conditions:
                            type: object
                            description: >-
                              Conditions for filtering results based on
                              metadata.
                            properties:
                              logical_operator:
                                type: string
                                enum:
                                  - and
                                  - or
                              conditions:
                                type: array
                                items:
                                  type: object
                                  properties:
                                    name:
                                      type: string
                                      description: Name of the metadata field.
                                    comparison_operator:
                                      type: string
                                      description: The operator for comparison.
                                    value:
                                      oneOf:
                                        - type: string
                                        - type: number
                                      nullable: true
                                      description: The value to compare against.
            required: true
            refIdentifier: '#/components/schemas/RetrieveRequest'
            requiredProperties:
              - query
        examples:
          example:
            value:
              query: <string>
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
                metadata_filtering_conditions:
                  logical_operator: and
                  conditions:
                    - name: <string>
                      comparison_operator: <string>
                      value: <string>
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              query:
                allOf:
                  - type: object
                    properties:
                      content:
                        type: string
              records:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/RetrievedSegment'
            refIdentifier: '#/components/schemas/RetrieveResponse'
        examples:
          example:
            value:
              query:
                content: <string>
              records:
                - segment:
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
                    document:
                      id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                      data_source_type: <string>
                      name: <string>
                  score: 123
        description: List of retrieved segments matching the query.
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
    RetrievedSegment:
      type: object
      properties:
        segment:
          allOf:
            - $ref: '#/components/schemas/Segment'
            - type: object
              properties:
                document:
                  type: object
                  properties:
                    id:
                      type: string
                      format: uuid
                    data_source_type:
                      type: string
                    name:
                      type: string
        score:
          type: number
          format: float

````