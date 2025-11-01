# Speech to Text

> Convert audio file to text. Supported formats: mp3, mp4, mpeg, mpga, m4a, wav, webm. File size limit: 15MB.

## OpenAPI

````yaml en/openapi_chatflow.json post /audio-to-text
paths:
  path: /audio-to-text
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
      multipart/form-data:
        schemaArray:
          - type: object
            properties:
              file:
                allOf:
                  - type: string
                    format: binary
                    description: >-
                      Audio file. Formats: mp3, mp4, mpeg, mpga, m4a, wav, webm.
                      Limit: 15MB.
              user:
                allOf:
                  - type: string
            required: true
            refIdentifier: '#/components/schemas/AudioToTextRequest'
            requiredProperties:
              - file
              - user
        examples:
          example:
            value:
              user: <string>
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              text:
                allOf:
                  - type: string
            refIdentifier: '#/components/schemas/AudioToTextResponse'
        examples:
          example:
            value:
              text: <string>
        description: Successfully converted audio to text.
  deprecated: false
  type: path
components:
  schemas: {}

````