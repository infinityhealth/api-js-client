Infinity API JS Client, generated using openapi-client-axios from the OpenAPI v3 definition and wrapped with neverthrow.

- [openapi-client-axios](https://github.com/openapistack/openapi-client-axios) - Generates the main API client using Axios
- [neverthrow](https://github.com/supermacro/neverthrow) - Used in to wrap API responses for easier error-handling

# Installation

Using your node runtime of choice install the package.

bun add @infinityhealth/api-js-client -D

# Usage

Create a file such as `client.ts` to store an instance of our JS Client.

```ts
import { init } from "@infinityhealth/api-js-client"

export const client = init("https://infinity-dev-api.infinity.health")
// ^ returns a full typed client, with autocomplete for all methods, parameters etc.
```

Then when needed, just import this `client` in project files as needed.

`init` takes the API base URL as an optional argument, otherwise it will default to the value defined in the OpenAPI definition.

```ts
import { client } from "some/path/to/client"

async function make_api_call() {
  const sso_configs = await client.get_sso_configs()
  // ^ returns a neverthrow Result with data from API call

  sso_configs.map((data) => {
    // ^ Use Result.map to work with an ok response
  })

  sso_configs.mapErr((errror) => {
    // ^ Use Result.mapErr to work with an error response
  })
}
```
