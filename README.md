# Ruby Serverless Integration Functions

Ruby AWS Lambda handlers that coordinate webhook-driven data between HiBob and Pinpoint services.

## Structure

- `lambda_function.rb` — Lambda entry point and event dispatch.
- `app/helpers/webhook_helpers.rb` — webhook parsing and shared response behavior.
- `app/services/hi_bob` — people and document operations.
- `app/services/pin_point` — application and comment operations.
- `serverless.yml` — function packaging and deployment configuration.

## Event flow

```text
webhook event -> Lambda handler -> provider-specific helper
                              -> HiBob / Pinpoint API service
                              -> normalized Lambda response
```

Install gems with `bundle install`, provide provider credentials and endpoint configuration through the deployment environment, then use the Serverless Framework commands defined by the project.

## Boundaries

Live provider calls, credential scopes, webhook authenticity, retries, idempotency, rate limits, and partial failure behavior require production validation. Use captured synthetic events and dry-run provider clients before any real deployment.
