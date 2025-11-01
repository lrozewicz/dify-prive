# Get Annotation List

## OpenAPI

````yaml en/openapi_chatflow.json get /apps/annotations
paths:
  path: /apps/annotations
  method: get
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
      query:
        page:
          schema:
            - type: integer
              description: Page number.
              default: 1
        limit:
          schema:
            - type: integer
              description: Number of items per page (Default 20, Max 100).
              maximum: 100
              minimum: 1
              default: 20
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
                      $ref: '#/components/schemas/AnnotationItem'
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
            refIdentifier: '#/components/schemas/AnnotationListResponse'
        examples:
          example:
            value:
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  question: <string>
                  answer: <string>
                  hit_count: 123
                  created_at: 123
              has_more: true
              limit: 123
              total: 123
              page: 123
        description: Annotation list.
  deprecated: false
  type: path
components:
  schemas:
    AnnotationItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        question:
          type: string
        answer:
          type: string
        hit_count:
          type: integer
        created_at:
          type: integer
          format: int64

````