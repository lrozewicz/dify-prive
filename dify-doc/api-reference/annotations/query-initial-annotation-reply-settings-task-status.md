# Query Initial Annotation Reply Settings Task Status

## OpenAPI

````yaml en/openapi_chatflow.json get /apps/annotation-reply/{action}/status/{job_id}
paths:
  path: /apps/annotation-reply/{action}/status/{job_id}
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
      path:
        action:
          schema:
            - type: enum<string>
              enum:
                - enable
                - disable
              required: true
              description: 'Action: ''enable'' or ''disable''.'
        job_id:
          schema:
            - type: string
              required: true
              description: Job ID.
              format: uuid
      query: {}
      header: {}
      cookie: {}
    body: {}
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              job_id:
                allOf:
                  - type: string
                    format: uuid
              job_status:
                allOf:
                  - type: string
              error_msg:
                allOf:
                  - type: string
                    nullable: true
            refIdentifier: '#/components/schemas/InitialAnnotationReplySettingsStatusResponse'
        examples:
          example:
            value:
              job_id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
              job_status: <string>
              error_msg: <string>
        description: Task status.
  deprecated: false
  type: path
components:
  schemas: {}

````