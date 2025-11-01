# File Preview

> Preview or download uploaded files. This endpoint allows you to access files that have been previously uploaded via the File Upload API. Files can only be accessed if they belong to messages within the requesting application.

## OpenAPI

````yaml en/openapi_workflow.json get /files/{file_id}/preview
paths:
  path: /files/{file_id}/preview
  method: get
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
      path:
        file_id:
          schema:
            - type: string
              required: true
              description: >-
                The unique identifier of the file to preview, obtained from the
                File Upload API response.
              format: uuid
      query:
        as_attachment:
          schema:
            - type: boolean
              required: false
              description: >-
                Whether to force download the file as an attachment. Default is
                `false` (preview in browser).
              default: false
      header: {}
      cookie: {}
    body: {}
  response:
    '200':
      image/png:
        schemaArray:
          - type: file
            contentEncoding: binary
        examples:
          example: {}
        description: >-
          File content returned successfully. Headers set based on file type and
          request parameters.
      image/jpeg:
        schemaArray:
          - type: file
            contentEncoding: binary
        examples:
          example: {}
        description: >-
          File content returned successfully. Headers set based on file type and
          request parameters.
      image/webp:
        schemaArray:
          - type: file
            contentEncoding: binary
        examples:
          example: {}
        description: >-
          File content returned successfully. Headers set based on file type and
          request parameters.
      image/gif:
        schemaArray:
          - type: file
            contentEncoding: binary
        examples:
          example: {}
        description: >-
          File content returned successfully. Headers set based on file type and
          request parameters.
      application/octet-stream:
        schemaArray:
          - type: file
            contentEncoding: binary
        examples:
          example: {}
        description: >-
          File content returned successfully. Headers set based on file type and
          request parameters.
    '400':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - &ref_0
                    type: integer
                    nullable: true
              code:
                allOf:
                  - &ref_1
                    type: string
                    nullable: true
              message:
                allOf:
                  - &ref_2
                    type: string
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: |-
          Bad Request. Possible error codes:
          - `invalid_param`: Abnormal parameter input.
    '403':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_0
              code:
                allOf:
                  - *ref_1
              message:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: >-
          Forbidden. Possible error codes:

          - `file_access_denied`: File access denied or file does not belong to
          current application.
    '404':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_0
              code:
                allOf:
                  - *ref_1
              message:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: |-
          Not Found. Possible error codes:
          - `file_not_found`: File not found or has been deleted.
    '500':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_0
              code:
                allOf:
                  - *ref_1
              message:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Internal server error.
  deprecated: false
  type: path
components:
  schemas: {}

````