# Send Chat Message

> Send a request to the chat application.

## OpenAPI

````yaml en/openapi_chat.json post /chat-messages
paths:
  path: /chat-messages
  method: post
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Chat App API. Replace {api_base_url} with the
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
    body:
      application/json:
        schemaArray:
          - type: object
            properties:
              query:
                allOf:
                  - type: string
                    description: User Input/Question content.
              inputs:
                allOf:
                  - type: object
                    description: >-
                      Allows the entry of various variable values defined by the
                      App. Contains key/value pairs. Default {}.
                    additionalProperties: true
                    default: {}
              response_mode:
                allOf:
                  - type: string
                    enum:
                      - streaming
                      - blocking
                    description: >-
                      Mode of response return. `streaming` (recommended) uses
                      SSE. `blocking` returns after completion (may be
                      interrupted for long processes; not supported in Agent
                      Assistant mode). Cloudflare timeout is 100s.
                    default: streaming
              user:
                allOf:
                  - type: string
                    description: >-
                      User identifier, unique within the application. **Note**:
                      The Service API does not share conversations created by
                      the WebApp. Conversations created through the API are
                      isolated from those created in the WebApp interface.
              conversation_id:
                allOf:
                  - type: string
                    description: >-
                      Conversation ID to continue a conversation. Pass the
                      previous message's conversation_id.
              files:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/InputFileObject'
                    description: File list (images) for Vision-capable models.
              auto_generate_name:
                allOf:
                  - type: boolean
                    description: >-
                      Auto-generate conversation title. Default `true`. If
                      `false`, use conversation rename API with `auto_generate:
                      true` for async title generation.
                    default: true
            required: true
            refIdentifier: '#/components/schemas/ChatRequest'
            requiredProperties:
              - query
              - user
        examples:
          streaming_example:
            summary: Streaming mode example with file
            value:
              inputs: {}
              query: What are the specs of the iPhone 13 Pro Max?
              response_mode: streaming
              conversation_id: ''
              user: abc-123
              files:
                - type: image
                  transfer_method: remote_url
                  url: https://cloud.dify.ai/logo/logo-site.png
        description: Request body to send a chat message.
  response:
    '200':
      application/json:
        schemaArray:
          - type: object
            properties:
              event:
                allOf:
                  - type: string
                    description: Event type, fixed as `message`.
                    example: message
              task_id:
                allOf:
                  - type: string
                    format: uuid
                    description: Task ID for request tracking and stop response API.
              id:
                allOf:
                  - type: string
                    format: uuid
                    description: Unique ID of this response/message event.
              message_id:
                allOf:
                  - type: string
                    format: uuid
                    description: Unique message ID.
              conversation_id:
                allOf:
                  - type: string
                    format: uuid
                    description: Conversation ID.
              mode:
                allOf:
                  - type: string
                    description: App mode, fixed as `chat`.
                    example: chat
              answer:
                allOf:
                  - type: string
                    description: Complete response content.
              metadata:
                allOf:
                  - type: object
                    properties:
                      usage:
                        $ref: '#/components/schemas/Usage'
                      retriever_resources:
                        type: array
                        items:
                          $ref: '#/components/schemas/RetrieverResource'
              created_at:
                allOf:
                  - type: integer
                    format: int64
                    description: Message creation timestamp (Unix epoch seconds).
            description: Response object for blocking mode chat completion.
            refIdentifier: '#/components/schemas/ChatCompletionResponse'
        examples:
          blockingResponse:
            summary: Example of a blocking mode response
            value:
              event: message
              task_id: c3800678-a077-43df-a102-53f23ed20b88
              id: 9da23599-e713-473b-982c-4328d4f5c78a
              message_id: 9da23599-e713-473b-982c-4328d4f5c78a
              conversation_id: 45701982-8118-4bc5-8e9b-64562b4555f2
              mode: chat
              answer: iPhone 13 Pro Max specs are listed here:...
              metadata:
                usage:
                  prompt_tokens: 1033
                  prompt_unit_price: '0.001'
                  prompt_price_unit: '0.001'
                  prompt_price: '0.0010330'
                  completion_tokens: 128
                  completion_unit_price: '0.002'
                  completion_price_unit: '0.001'
                  completion_price: '0.0002560'
                  total_tokens: 1161
                  total_price: '0.0012890'
                  currency: USD
                  latency: 0.7682376249867957
                retriever_resources:
                  - position: 1
                    dataset_id: 101b4c97-fc2e-463c-90b1-5261a4cdcafb
                    dataset_name: iPhone
                    document_id: 8dd1ad74-0b5f-4175-b735-7d98bbbb4e00
                    document_name: iPhone List
                    segment_id: ed599c7f-2766-4294-9d1d-e5235a61270a
                    score: 0.98457545
                    content: >-
                      "Model","Release Date","Display
                      Size","Resolution","Processor","RAM","Storage","Camera","Battery","Operating
                      System"

                      "iPhone 13 Pro Max","September 24, 2021","6.7 inch","1284
                      x 2778","Hexa-core (2x3.23 GHz Avalanche + 4x1.82 GHz
                      Blizzard)","6 GB","128, 256, 512 GB, 1TB","12 MP","4352
                      mAh","iOS 15"
              created_at: 1705407629
        description: >-
          Successful response. The content type and structure depend on the
          `response_mode` parameter in the request.

          - If `response_mode` is `blocking`, returns `application/json` with a
          `ChatCompletionResponse` object.

          - If `response_mode` is `streaming`, returns `text/event-stream` with
          a stream of `ChunkChatEvent` objects.
      text/event-stream:
        schemaArray:
          - type: string
            description: >-
              A stream of Server-Sent Events. Each event is a JSON object
              prefixed with 'data: ' and suffixed with '\n\n'. See
              `ChunkChatEvent` for possible event structures.
        examples:
          streamingResponseBasic:
            summary: Example of a streaming mode response (Basic Assistant)
            value: >+
              data: {"event": "message", "task_id":"mock_task_id", "message_id":
              "5ad4cb98-f0c7-4085-b384-88c403be6290", "conversation_id":
              "45701982-8118-4bc5-8e9b-64562b4555f2", "answer": " I",
              "created_at": 1679586595}


              data: {"event": "message_end", "task_id":"mock_task_id",
              "message_id": "5ad4cb98-f0c7-4085-b384-88c403be6290",
              "conversation_id": "45701982-8118-4bc5-8e9b-64562b4555f2",
              "metadata": {"usage": {"total_tokens": 10, "latency": 1.0}}}

          streamingResponseAgent:
            summary: >-
              Example of a streaming mode response (Agent Assistant with
              agent_thought and message_file)
            value: >+
              data: {"event": "agent_thought", "id": "agent_thought_id_1",
              "task_id": "task123", "message_id": "msg123", "conversation_id":
              "conv123", "position": 1, "thought": "Thinking about calling a
              tool...", "tool": "dalle3", "tool_input": "{\"dalle3\":
              {\"prompt\": \"a cute cat\"}}", "created_at": 1705395332}


              data: {"event": "message_file", "id": "file_id_1", "type":
              "image", "belongs_to": "assistant", "url":
              "https://example.com/cat.png", "conversation_id": "conv123"}


              data: {"event": "agent_message", "task_id": "task123",
              "message_id": "msg123", "conversation_id": "conv123", "answer":
              "Here is the image: ", "created_at": 1705395333}


              data: {"event": "message_end", "task_id":"task123", "message_id":
              "msg123", "conversation_id": "conv123", "metadata": {"usage":
              {"total_tokens": 50, "latency": 2.5}}}

        description: >-
          Successful response. The content type and structure depend on the
          `response_mode` parameter in the request.

          - If `response_mode` is `blocking`, returns `application/json` with a
          `ChatCompletionResponse` object.

          - If `response_mode` is `streaming`, returns `text/event-stream` with
          a stream of `ChunkChatEvent` objects.
    '400':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - &ref_0
                    type: integer
              code:
                allOf:
                  - &ref_1
                    type: string
              message:
                allOf:
                  - &ref_2
                    type: string
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: >-
          Bad Request. Possible error codes:

          - `invalid_param`: Abnormal parameter input.

          - `app_unavailable`: App configuration unavailable.

          - `provider_not_initialize`: No available model credential
          configuration.

          - `provider_quota_exceeded`: Model invocation quota insufficient.

          - `model_currently_not_support`: Current model unavailable.

          - `completion_request_error`: Text generation failed.
    '404':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_0
              code:
                allOf:
                  - *ref_1
              message:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Conversation does not exist.
    '500':
      application/json:
        schemaArray:
          - type: object
            properties:
              status:
                allOf:
                  - *ref_0
              code:
                allOf:
                  - *ref_1
              message:
                allOf:
                  - *ref_2
            refIdentifier: '#/components/schemas/ErrorResponse'
        examples:
          example:
            value:
              status: 123
              code: <string>
              message: <string>
        description: Internal server error.
  deprecated: false
  type: path
components:
  schemas:
    InputFileObject:
      type: object
      required:
        - type
        - transfer_method
      properties:
        type:
          type: string
          enum:
            - image
          description: 'Supported type: `image`.'
        transfer_method:
          type: string
          enum:
            - remote_url
            - local_file
          description: >-
            Transfer method, `remote_url` for image URL / `local_file` for file
            upload
        url:
          type: string
          format: url
          description: Image URL (when the transfer method is `remote_url`)
        upload_file_id:
          type: string
          description: >-
            Uploaded file ID, which must be obtained by uploading through the
            File Upload API in advance (when the transfer method is
            `local_file`)
      anyOf:
        - properties:
            transfer_method:
              enum:
                - remote_url
            url:
              type: string
              format: url
          required:
            - url
          not:
            required:
              - upload_file_id
        - properties:
            transfer_method:
              enum:
                - local_file
            upload_file_id:
              type: string
          required:
            - upload_file_id
          not:
            required:
              - url
    Usage:
      type: object
      description: Model usage information.
      properties:
        prompt_tokens:
          type: integer
        prompt_unit_price:
          type: string
          format: decimal
        prompt_price_unit:
          type: string
          format: decimal
        prompt_price:
          type: string
          format: decimal
        completion_tokens:
          type: integer
        completion_unit_price:
          type: string
          format: decimal
        completion_price_unit:
          type: string
          format: decimal
        completion_price:
          type: string
          format: decimal
        total_tokens:
          type: integer
        total_price:
          type: string
          format: decimal
        currency:
          type: string
          example: USD
        latency:
          type: number
          format: double
    RetrieverResource:
      type: object
      description: Citation and Attribution information for a resource.
      properties:
        position:
          type: integer
          description: Position of the resource in the list.
        dataset_id:
          type: string
          format: uuid
          description: ID of the dataset.
        dataset_name:
          type: string
          description: Name of the dataset.
        document_id:
          type: string
          format: uuid
          description: ID of the document.
        document_name:
          type: string
          description: Name of the document.
        segment_id:
          type: string
          format: uuid
          description: ID of the specific segment within the document.
        score:
          type: number
          format: float
          description: Relevance score of the resource.
        content:
          type: string
          description: Content snippet from the resource.

````