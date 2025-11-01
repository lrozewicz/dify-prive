# Get Application Basic Information

> Used to get basic information about this application.

## OpenAPI

````yaml en/openapi_completion.json get /info
paths:
  path: /info
  method: get
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Completion App API. Replace {api_base_url} with the
        actual API base URL provided for your application (e.g., from
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
              description: >-
                API Key authentication. For all API requests, include your API
                Key in the `Authorization` HTTP Header, prefixed with 'Bearer '.
                Example: `Authorization: Bearer {API_KEY}`. **Strongly recommend
                storing your API Key on the server-side, not shared or stored on
                the client-side, to avoid possible API-Key leakage that can lead
                to serious consequences.**
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
              name:
                allOf:
                  - type: string
                    description: Application name.
              description:
                allOf:
                  - type: string
                    description: Application description.
              tags:
                allOf:
                  - type: array
                    items:
                      type: string
                    description: Application tags.
            refIdentifier: '#/components/schemas/AppInfoResponse'
        examples:
          success:
            value:
              name: My App
              description: This is my app.
              tags:
                - tag1
                - tag2
        description: Basic information of the application.
  deprecated: false
  type: path
components:
  schemas: {}

````