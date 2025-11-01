# File Upload for Workflow

> Upload a file for use in workflows. Supports any formats supported by your workflow. Uploaded files are for the current end-user only.

## OpenAPI

````yaml en/openapi_workflow.json post /files/upload
paths:
  path: /files/upload
  method: post
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Workflow App API. Replace {api_base_url} with the
        actual API base URL.
      variables:
        api_base_url:
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
              description: API Key authentication.
          cookie: {}
    parameters:
      path: {}
      query: {}
      header: {}
      cookie: {}
    body:
      multipart/form-data:
        schemaArray:
          - type: object
            properties:
              file:
                allOf:
                  - type: string
                    format: binary
                    description: The file to be uploaded.
              user:
                allOf:
                  - type: string
                    description: User identifier.
            required: true
            requiredProperties:
              - file
              - user
        examples:
          example:
            value:
              user: <string>
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              id:
                allOf:
                  - &ref_0
                    type: string
                    format: uuid
              name:
                allOf:
                  - &ref_1
                    type: string
              size:
                allOf:
                  - &ref_2
                    type: integer
              extension:
                allOf:
                  - &ref_3
                    type: string
              mime_type:
                allOf:
                  - &ref_4
                    type: string
              created_by:
                allOf:
                  - &ref_5
                    type: string
                    format: uuid
              created_at:
                allOf:
                  - &ref_6
                    type: integer
                    format: int64
            refIdentifier: '#/components/schemas/FileUploadResponse'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              name: <string>
              size: 123
              extension: <string>
              mime_type: <string>
              created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              created_at: 123
        description: File uploaded successfully.
    '201':
      application/json:
        schemaArray:
          - type: object
            properties:
              id:
                allOf:
                  - *ref_0
              name:
                allOf:
                  - *ref_1
              size:
                allOf:
                  - *ref_2
              extension:
                allOf:
                  - *ref_3
              mime_type:
                allOf:
                  - *ref_4
              created_by:
                allOf:
                  - *ref_5
              created_at:
                allOf:
                  - *ref_6
            refIdentifier: '#/components/schemas/FileUploadResponse'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              name: <string>
              size: 123
              extension: <string>
              mime_type: <string>
              created_by: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              created_at: 123
        description: File created successfully (alternative success code).
    '400':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - &ref_7
                    type: integer
                    nullable: true
              code:
                allOf:
                  - &ref_8
                    type: string
                    nullable: true
              message:
                allOf:
                  - &ref_9
                    type: string
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Bad Request for file operation.
    '413':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_7
              code:
                allOf:
                  - *ref_8
              message:
                allOf:
                  - *ref_9
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: File is too large.
    '415':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_7
              code:
                allOf:
                  - *ref_8
              message:
                allOf:
                  - *ref_9
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Unsupported file type for upload.
    '500':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_7
              code:
                allOf:
                  - *ref_8
              message:
                allOf:
                  - *ref_9
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Internal server error.
    '503':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_7
              code:
                allOf:
                  - *ref_8
              message:
                allOf:
                  - *ref_9
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: S3 storage error.
  deprecated: false
  type: path
components:
  schemas: {}

````