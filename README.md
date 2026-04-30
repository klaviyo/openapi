# Klaviyo's OpenAPI Specification

Versioned [OpenAPI specs](openapi/stable.json) for the Klaviyo API. Same source we use for [API docs](https://developers.klaviyo.com/en/reference/) and our [SDKs](https://developers.klaviyo.com/en/docs/sdk_overview).

## Layout

| Path | Contents | Use it when |
|---|---|---|
| `openapi/stable.json` | Full GA spec (~2.5 MB, all operations across all categories) | SDK codegen, full validation, anything needing the complete surface |
| `openapi/stable/categories/{category}.json` | Per-category slice — e.g. `forms.json`, `profiles.json`, `templates.json`, `reporting.json` | Grounding an LLM against a single category; partner integrations scoped to one category |
| `openapi/stable/apis/{operationId}.json` | Per-endpoint slice — e.g. `create_form.json`, `get_profile.json` | Tooling that operates on a single endpoint at a time |
| `openapi/beta.json` and `openapi/beta/{categories,apis}/...` | Same layout for pre-release endpoints | Testing forthcoming APIs before GA |

`operationId` matches the [developer portal](https://developers.klaviyo.com/en/reference/) URL slug 1:1 — `/en/reference/create_form` ↔ `openapi/stable/apis/create_form.json`.

## LLM agents — use the per-category slice

The full spec is too large for many WebFetch-style tools to consume reliably. Per-category slices (~50–200 KB) are self-contained OpenAPI 3 documents with all referenced components inlined and `$ref` semantics preserved.

Examples:

- Forms → `openapi/stable/categories/forms.json`
- Templates → `openapi/stable/categories/templates.json`
- Profiles → `openapi/stable/categories/profiles.json`

Raw URLs (for `curl`, WebFetch, or grounding tools):

```
https://raw.githubusercontent.com/klaviyo/openapi/main/openapi/stable/categories/forms.json
https://raw.githubusercontent.com/klaviyo/openapi/main/openapi/stable/apis/create_form.json
```

## Revisions

Each API revision (e.g. `2026-04-15`) lives on its own branch. The `main` branch tracks the latest GA revision.

## Legacy

Legacy spec: https://klaviyo-openapi.s3.amazonaws.com/spec.json
