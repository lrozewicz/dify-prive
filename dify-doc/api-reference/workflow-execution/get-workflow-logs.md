# Get Workflow Logs

> Returns workflow logs, with the first page returning the latest `{limit}` messages, i.e., in reverse order.

## OpenAPI

````yaml en/openapi_workflow.json get /workflows/logs
paths:
  path: /workflows/logs
  method: get
  servers:
    - url: '{api_base_url}'
      description: >-
        The base URL for the Workflow App API. Replace {api_base_url} with the
        actual API base URL.
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
        keyword:
          schema:
            - type: string
              description: Keyword to search.
        status:
          schema:
            - type: enum<string>
              enum:
                - succeeded
                - failed
                - stopped
                - running
              description: Filter by status.
        page:
          schema:
            - type: integer
              description: Current page.
              default: 1
        limit:
          schema:
            - type: integer
              description: Number of items per page.
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
              page:
                allOf:
                  - type: integer
              limit:
                allOf:
                  - type: integer
              total:
                allOf:
                  - type: integer
              has_more:
                allOf:
                  - type: boolean
              data:
                allOf:
                  - type: array
                    items:
                      $ref: '#/components/schemas/WorkflowLogItem'
            refIdentifier: '#/components/schemas/WorkflowLogsResponse'
        examples:
          example:
            value:
              page: 123
              limit: 123
              total: 123
              has_more: true
              data:
                - id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  workflow_run:
                    id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                    version: <string>
                    status: running
                    error: <string>
                    elapsed_time: 123
                    total_tokens: 123
                    total_steps: 123
                    created_at: 123
                    finished_at: 123
                  created_from: <string>
                  created_by_role: <string>
                  created_by_account: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                  created_by_end_user:
                    id: 3c90c3cc-0d44-4b50-8888-8dd25736052a
                    type: <string>
                    is_anonymous: true
                    session_id: <string>
                  created_at: 123
        description: Successfully retrieved workflow logs.
  deprecated: false
  type: path
components:
  schemas:
    WorkflowLogItem:
      type: object
      properties:
        id:
          type: string
          format: uuid
        workflow_run:
          $ref: '#/components/schemas/WorkflowRunSummary'
        created_from:
          type: string
        created_by_role:
          type: string
        created_by_account:
          type: string
          format: uuid
          nullable: true
        created_by_end_user:
          $ref: '#/components/schemas/EndUserSummary'
        created_at:
          type: integer
          format: int64
    WorkflowRunSummary:
      type: object
      properties:
        id:
          type: string
          format: uuid
        version:
          type: string
        status:
          type: string
          enum:
            - running
            - succeeded
            - failed
            - stopped
        error:
          type: string
          nullable: true
        elapsed_time:
          type: number
          format: float
        total_tokens:
          type: integer
        total_steps:
          type: integer
        created_at:
          type: integer
          format: int64
        finished_at:
          type: integer
          format: int64
          nullable: true
    EndUserSummary:
      type: object
      properties:
        id:
          type: string
          format: uuid
        type:
          type: string
        is_anonymous:
          type: boolean
        session_id:
          type: string

````