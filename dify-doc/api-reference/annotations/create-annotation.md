# Create Annotation

## OpenAPI

````yaml en/openapi_chatflow.json post /apps/annotations
paths:
  path: /apps/annotations
  method: post
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Advanced Chat App API. Replace {api_base_url} with
        the actual API base URL provided for your application (e.g., from
        props.appDetail.api_base_url).
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
      application/json:
        schemaArray:
          - type: object
            properties:
              question:
                allOf:
                  - type: string
              answer:
                allOf:
                  - type: string
            required: true
            refIdentifier: '#/components/schemas/CreateAnnotationRequest'
            requiredProperties:
              - question
              - answer
        examples:
          example:
            value:
              question: <string>
              answer: <string>
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
              question:
                allOf:
                  - &ref_1
                    type: string
              answer:
                allOf:
                  - &ref_2
                    type: string
              hit_count:
                allOf:
                  - &ref_3
                    type: integer
              created_at:
                allOf:
                  - &ref_4
                    type: integer
                    format: int64
            refIdentifier: '#/components/schemas/AnnotationItem'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              question: <string>
              answer: <string>
              hit_count: 123
              created_at: 123
        description: Annotation created.
    '201':
      application/json:
        schemaArray:
          - type: object
            properties:
              id:
                allOf:
                  - *ref_0
              question:
                allOf:
                  - *ref_1
              answer:
                allOf:
                  - *ref_2
              hit_count:
                allOf:
                  - *ref_3
              created_at:
                allOf:
                  - *ref_4
            refIdentifier: '#/components/schemas/AnnotationItem'
        examples:
          example:
            value:
              id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              question: <string>
              answer: <string>
              hit_count: 123
              created_at: 123
        description: Annotation created.
  deprecated: false
  type: path
components:
  schemas: {}

````