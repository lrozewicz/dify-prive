# Delete Annotation

## OpenAPI

````yaml en/openapi_chatflow.json delete /apps/annotations/{annotation_id}
paths:
  path: /apps/annotations/{annotation_id}
  method: delete
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
    body: {}
  response:
    '204':
      _mintlify/placeholder:
        schemaArray:
          - type: any
            description: Annotation deleted.
        examples: {}
        description: Annotation deleted.
  deprecated: false
  type: path
components:
  schemas: {}

````