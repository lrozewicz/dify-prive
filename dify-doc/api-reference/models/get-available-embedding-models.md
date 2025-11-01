# Get available embedding models

> Fetches a list of all available text embedding models that can be used for creating and querying knowledge bases.

## OpenAPI

````yaml en/openapi_knowledge.json get /workspaces/current/models/model-types/text-embedding
paths:
  path: /workspaces/current/models/model-types/text-embedding
  method: get
  servers:
    - url: '{apiBaseUrl}'
      description: The base URL for the Knowledge API.
      variables:
        apiBaseUrl:
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
              data:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/ModelProvider'
        examples:
          example:
            value:
              data:
                - provider: <string>
                  label: {}
                  icon_small: {}
                  icon_large: {}
                  status: <string>
                  models:
                    - model: <string>
                      label: {}
                      model_type: <string>
                      features:
                        - <any>
                      fetch_from: <string>
                      model_properties:
                        context_size: 123
                      deprecated: true
                      status: <string>
                      load_balancing_enabled: true
        description: A list of available embedding models grouped by provider.
  deprecated: false
  type: path
components:
  schemas:
    Model:
      type: object
      properties:
        model:
          type: string
        label:
          type: object
          additionalProperties:
            type: string
        model_type:
          type: string
        features:
          type: array
          items: {}
          nullable: true
        fetch_from:
          type: string
        model_properties:
          type: object
          properties:
            context_size:
              type: integer
        deprecated:
          type: boolean
        status:
          type: string
        load_balancing_enabled:
          type: boolean
    ModelProvider:
      type: object
      properties:
        provider:
          type: string
        label:
          type: object
          additionalProperties:
            type: string
        icon_small:
          type: object
          additionalProperties:
            type: string
            format: uri
        icon_large:
          type: object
          additionalProperties:
            type: string
            format: uri
        status:
          type: string
        models:
          type: array
          items:
            $ref: '#/components/schemas/Model'

````