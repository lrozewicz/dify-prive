# Get Application Parameters Information

> Used at the start of entering the page to obtain information such as features, input parameter names, types, and default values.

## OpenAPI

````yaml en/openapi_completion.json get /parameters
paths:
  path: /parameters
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
              opening_statement:
                allOf:
                  - type: string
                    description: Opening statement.
              suggested_questions:
                allOf:
                  - type: array
                    items:
                      type: string
                    description: List of suggested questions for the opening.
              suggested_questions_after_answer:
                allOf:
                  - type: object
                    properties:
                      enabled:
                        type: boolean
                        description: >-
                          Whether suggesting questions after an answer is
                          enabled.
              speech_to_text:
                allOf:
                  - type: object
                    properties:
                      enabled:
                        type: boolean
                        description: Whether speech to text is enabled.
              retriever_resource:
                allOf:
                  - type: object
                    properties:
                      enabled:
                        type: boolean
                        description: >-
                          Whether citation and attribution (retriever resource)
                          is enabled.
              annotation_reply:
                allOf:
                  - type: object
                    properties:
                      enabled:
                        type: boolean
                        description: Whether annotation reply is enabled.
              user_input_form:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/UserInputFormItem'
                    description: User input form configuration.
              file_upload:
                allOf:
                  - type: object
                    description: File upload configuration.
                    properties:
                      image:
                        type: object
                        description: >-
                          Image settings. Currently only supports image types:
                          png, jpg, jpeg, webp, gif.
                        properties:
                          enabled:
                            type: boolean
                            description: Whether image upload is enabled.
                          number_limits:
                            type: integer
                            description: Image number limit, default is 3.
                          detail:
                            type: string
                            description: >-
                              Detail level for image processing (e.g., 'high').
                              From example, not in main description.
                          transfer_methods:
                            type: array
                            items:
                              type: string
                              enum:
                                - remote_url
                                - local_file
                            description: >-
                              List of transfer methods, must choose at least one
                              if enabled.
              system_parameters:
                allOf:
                  - type: object
                    description: System parameters.
                    properties:
                      file_size_limit:
                        type: integer
                        description: Document upload size limit (MB).
                      image_file_size_limit:
                        type: integer
                        description: Image file upload size limit (MB).
                      audio_file_size_limit:
                        type: integer
                        description: Audio file upload size limit (MB).
                      video_file_size_limit:
                        type: integer
                        description: Video file upload size limit (MB).
            refIdentifier: '#/components/schemas/AppParametersResponse'
        examples:
          success:
            value:
              opening_statement: Hello!
              suggested_questions_after_answer:
                enabled: true
              speech_to_text:
                enabled: true
              retriever_resource:
                enabled: true
              annotation_reply:
                enabled: true
              user_input_form:
                - paragraph:
                    label: Query
                    variable: query
                    required: true
                    default: ''
              file_upload:
                image:
                  enabled: false
                  number_limits: 3
                  detail: high
                  transfer_methods:
                    - remote_url
                    - local_file
              system_parameters:
                file_size_limit: 15
                image_file_size_limit: 10
                audio_file_size_limit: 50
                video_file_size_limit: 100
        description: Application parameters information.
  deprecated: false
  type: path
components:
  schemas:
    UserInputFormItem:
      type: object
      description: >-
        Represents a single item in the user input form. It will have one of the
        specific control type keys.
      oneOf:
        - $ref: '#/components/schemas/TextInputControlWrapper'
        - $ref: '#/components/schemas/ParagraphControlWrapper'
        - $ref: '#/components/schemas/SelectControlWrapper'
    TextInputControlWrapper:
      type: object
      properties:
        text-input:
          $ref: '#/components/schemas/TextInputControl'
      required:
        - text-input
    ParagraphControlWrapper:
      type: object
      properties:
        paragraph:
          $ref: '#/components/schemas/ParagraphControl'
      required:
        - paragraph
    SelectControlWrapper:
      type: object
      properties:
        select:
          $ref: '#/components/schemas/SelectControl'
      required:
        - select
    TextInputControl:
      type: object
      description: Text input control.
      properties:
        label:
          type: string
          description: Variable display label name.
        variable:
          type: string
          description: Variable ID.
        required:
          type: boolean
          description: Whether it is required.
        default:
          type: string
          description: Default value.
      required:
        - label
        - variable
        - required
    ParagraphControl:
      type: object
      description: Paragraph text input control.
      properties:
        label:
          type: string
          description: Variable display label name.
        variable:
          type: string
          description: Variable ID.
        required:
          type: boolean
          description: Whether it is required.
        default:
          type: string
          description: Default value.
      required:
        - label
        - variable
        - required
    SelectControl:
      type: object
      description: Dropdown control.
      properties:
        label:
          type: string
          description: Variable display label name.
        variable:
          type: string
          description: Variable ID.
        required:
          type: boolean
          description: Whether it is required.
        default:
          type: string
          description: Default value.
        options:
          type: array
          items:
            type: string
          description: Option values.
      required:
        - label
        - variable
        - required
        - options

````