# Update Annotation

## OpenAPI

````yaml en/openapi_chatflow.json put /apps/annotations/{annotation_id}
paths:
  path: /apps/annotations/{annotation_id}
  method: put
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
      path:
        annotation_id:
          schema:
            - type: string
              required: true
              description: Annotation ID.
              format: uuid
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
            refIdentifier: '#/components/schemas/UpdateAnnotationRequest'
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
                  - type: string
                    format: uuid
              question:
                allOf:
                  - type: string
              answer:
                allOf:
                  - type: string
              hit_count:
                allOf:
                  - type: integer
              created_at:
                allOf:
                  - type: integer
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
        description: Annotation updated.
  deprecated: false
  type: path
components:
  schemas: {}

````