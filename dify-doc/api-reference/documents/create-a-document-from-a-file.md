# Create a Document from a File

> Creates a new document within an existing knowledge base by uploading a file.

## OpenAPI

````yaml en/openapi_knowledge.json post /datasets/{dataset_id}/document/create-by-file
paths:
  path: /datasets/{dataset_id}/document/create-by-file
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
      multipart/form-data:
        schemaArray:
          - type: object
            properties:
              data:
                allOf:
                  - type: string
                    description: >-
                      A JSON string containing document metadata and processing
                      rules. See `CreateDocumentByFileRequestData` schema for
                      details.
                    example: >-
                      {"indexing_technique":"high_quality","process_rule":{"mode":"custom",
                      "rules": { "segmentation": {"separator":"###",
                      "max_tokens":500}}}}
              file:
                allOf:
                  - type: string
                    format: binary
                    description: The file to upload.
            required: true
        examples:
          example:
            value:
              data: >-
                {"indexing_technique":"high_quality","process_rule":{"mode":"custom",
                "rules": { "segmentation": {"separator":"###",
                "max_tokens":500}}}}
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
    '400':
      application/json:
        schemaArray:
          - type: object
            properties:
              code:
                allOf:
                  - &ref_0
                    type: string
                    description: A machine-readable error code.
              message:
                allOf:
                  - &ref_1
                    type: string
                    description: A human-readable error message.
              status:
                allOf:
                  - &ref_2
                    type: integer
                    description: The HTTP status code.
            refIdentifier: '#/components/schemas/ErrorResponse'
            example: &ref_3
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        examples:
          example:
            value:
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        description: >-
          Bad request related to file upload. Could be `no_file_uploaded` or
          `too_many_files`.
    '413':
      application/json:
        schemaArray:
          - type: object
            properties:
              code:
                allOf:
                  - *ref_0
              message:
                allOf:
                  - *ref_1
              status:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
            example: *ref_3
        examples:
          example:
            value:
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        description: File size exceeded.
    '415':
      application/json:
        schemaArray:
          - type: object
            properties:
              code:
                allOf:
                  - *ref_0
              message:
                allOf:
                  - *ref_1
              status:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
            example: *ref_3
        examples:
          example:
            value:
              code: no_file_uploaded
              message: Please upload your file.
              status: 400
        description: File type not allowed.
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