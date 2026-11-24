# CenterEdge.TextPay

Note: TextPay (a.k.a. DashNow) is now known as Hyfin.

OpenAPI 3.0 spec based on [Hyfin documentation](https://centeredge.hyfin.app/docs/2.0c/introduction). 

## Editing the spec

The SDK is generated from `swagger.json` with [Yardarm](https://github.com/CenterEdge/Yardarm). The spec is written by hand, so follow these conventions to keep the generated SDK valid:

- **Define shared enums once.** When more than one schema uses the same enum, add it under `components/schemas` and reference it with `$ref` (for example, `AddUpdateAction`). Repeating an inline enum under the same property name in two schemas generates two types with the same short name, and the System.Text.Json source-generated context drops one of their nullable forms, which fails deserialization at runtime.
- **Objects with only additional properties become dictionaries.** An object with no declared `properties` and `additionalProperties: true` generates `Dictionary<string, object?>`, not a class (for example, `Gateway.gateway_fields`). Declare its known properties if a class is needed.
