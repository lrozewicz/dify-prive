# Get Application Meta Information

## OpenAPI

````yaml en/openapi_chatflow.json get /meta
paths:
  path: /meta
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
              tool_icons:
                allOf:
                  - type: object
                    additionalProperties:
                      oneOf:
                        - type: string
                          format: url
                        - $ref: '#/components/schemas/ToolIconDetail'
            refIdentifier: '#/components/schemas/AppMetaResponse'
        examples:
          example:
            value:
              tool_icons: {}
        description: Application meta information (tool icons).
  deprecated: false
  type: path
components:
  schemas:
    ToolIconDetail:
      type: object
      properties:
        background:
          type: string
        content:
          type: string

````