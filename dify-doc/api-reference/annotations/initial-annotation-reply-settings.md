# Initial Annotation Reply Settings

## OpenAPI

````yaml en/openapi_chatflow.json post /apps/annotation-reply/{action}
paths:
  path: /apps/annotation-reply/{action}
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
      path:
        action:
          schema:
            - type: enum<string>
              enum:
                - enable
                - disable
              required: true
              description: 'Action: ''enable'' or ''disable''.'
      query: {}
      header: {}
      cookie: {}
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              embedding_provider_name:
                allOf:
                  - type: string
                    nullable: true
              embedding_model_name:
                allOf:
                  - type: string
                    nullable: true
              score_threshold:
                allOf:
                  - type: number
                    format: float
            required: true
            refIdentifier: '#/components/schemas/InitialAnnotationReplySettingsRequest'
            requiredProperties:
              - score_threshold
        examples:
          example:
            value:
              embedding_provider_name: <string>
              embedding_model_name: <string>
              score_threshold: 123
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              job_id:
                allOf:
                  - &ref_0
                    type: string
                    format: uuid
              job_status:
                allOf:
                  - &ref_1
                    type: string
            refIdentifier: '#/components/schemas/InitialAnnotationReplySettingsResponse'
        examples:
          example:
            value:
              job_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              job_status: <string>
        description: Task initiated.
    '202':
      application/json:
        schemaArray:
          - type: object
            properties:
              job_id:
                allOf:
                  - *ref_0
              job_status:
                allOf:
                  - *ref_1
            refIdentifier: '#/components/schemas/InitialAnnotationReplySettingsResponse'
        examples:
          example:
            value:
              job_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              job_status: <string>
        description: Task accepted.
  deprecated: false
  type: path
components:
  schemas: {}

````