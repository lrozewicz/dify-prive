# Create a Document from Text

> Creates a new document within an existing knowledge base directly from text content.

## OpenAPI

````yaml en/openapi_knowledge.json post /datasets/{dataset_id}/document/create-by-text
paths:
  path: /datasets/{dataset_id}/document/create-by-text
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
              description: The ID of the knowledge base to add the document to.
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
                    description: Name of the document.
              text:
                allOf:
                  - type: string
                    description: Full text content of the document.
              indexing_technique:
                allOf:
                  - type: string
                    description: Indexing technique for the document.
                    enum:
                      - high_quality
                      - economy
              doc_form:
                allOf:
                  - type: string
                    description: Format of the indexed content.
                    enum:
                      - text_model
                      - hierarchical_model
                      - qa_model
              doc_language:
                allOf:
                  - type: string
                    description: Language of the document, important for Q&A mode.
                    example: English
              process_rule:
                allOf:
                  - $ref: '#/components/schemas/ProcessRule'
              retrieval_model:
                allOf:
                  - $ref: '#/components/schemas/RetrievalModel'
              embedding_model:
                allOf:
                  - type: string
                    description: Name of the embedding model to use.
              embedding_model_provider:
                allOf:
                  - type: string
                    description: Provider of the embedding model.
            required: true
            refIdentifier: '#/components/schemas/CreateDocumentByTextRequest'
            requiredProperties:
              - name
              - text
        examples:
          example:
            value:
              name: <string>
              text: <string>
              indexing_technique: high_quality
              doc_form: text_model
              doc_language: English
              process_rule:
                mode: automatic
                rules:
                  pre_processing_rules:
                    - id: remove_extra_spaces
                      enabled: true
                  segmentation:
                    separator: <string>
                    max_tokens: 123
                  parent_mode: full-doc
                  subchunk_segmentation:
                    separator: <string>
                    max_tokens: 123
                    chunk_overlap: 123
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
              embedding_model: <string>
              embedding_model_provider: <string>
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              document:
                allOf:
                  - $ref: '#/components/schemas/Document'
              batch:
                allOf:
                  - type: string
                    description: A batch identifier for tracking indexing progress.
            refIdentifier: '#/components/schemas/DocumentCreationResponse'
        examples:
          example:
            value:
              document:
                id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
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
              batch: <string>
        description: Document created successfully and is being indexed.
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
    PreprocessingRule:
      type: object
      description: A rule for preprocessing document content.
      properties:
        id:
          type: string
          description: The unique identifier for the preprocessing rule.
          enum:
            - remove_extra_spaces
            - remove_urls_emails
        enabled:
          type: boolean
          description: Whether this rule is enabled.
    SegmentationRule:
      type: object
      description: Rules for segmenting document content into chunks.
      properties:
        separator:
          type: string
          description: The custom delimiter used to separate segments.
        max_tokens:
          type: integer
          description: The maximum number of tokens allowed in a single segment.
    SubChunkSegmentationRule:
      type: object
      description: >-
        Rules for segmenting parent chunks into smaller child chunks (for
        hierarchical mode).
      properties:
        separator:
          type: string
          description: The delimiter for sub-chunking.
        max_tokens:
          type: integer
          description: The maximum token length for a sub-chunk.
        chunk_overlap:
          type: integer
          description: The number of overlapping tokens between adjacent sub-chunks.
    ProcessRule:
      type: object
      description: >-
        A set of rules for processing a document, including cleaning and
        segmentation.
      properties:
        mode:
          type: string
          description: 'The processing mode: automatic, custom, or hierarchical.'
          enum:
            - automatic
            - custom
            - hierarchical
        rules:
          type: object
          description: >-
            The specific rules to apply, used when mode is 'custom' or
            'hierarchical'.
          properties:
            pre_processing_rules:
              type: array
              items:
                $ref: '#/components/schemas/PreprocessingRule'
            segmentation:
              $ref: '#/components/schemas/SegmentationRule'
            parent_mode:
              type: string
              description: Retrieval mode for parent chunks in hierarchical mode.
              enum:
                - full-doc
                - paragraph
            subchunk_segmentation:
              $ref: '#/components/schemas/SubChunkSegmentationRule'
          nullable: true
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