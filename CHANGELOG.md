For our complete changelog, and more, see our [dev portal](https://developers.klaviyo.com/en/docs/changelog_): 

# Revision `2023-02-22`
### New endpoints
* [Campaigns](ref:campaigns): Use our new Campaigns API endpoints to programmatically create, update, delete, and send email campaigns. See the API reference documentation for more info. We plan to introduce SMS support in the future.

> ❗️ Breaking changes
>
> * Updated [Flows](ref:flows) endpoints to use cursor-based pagination. This change brings flows pagination to parity with our other API endpoints. You can learn more about cursor-based pagination in our [API Overview](ref:api_overview#pagination).
> * Profile fields can now be nulled out by passing `null` into a profile field via the [Update Profile](ref:update_profile) endpoint.

# Revision `2023-01-24`

### New endpoints
* [Tags](ref:tags): Use our new Tags API endpoints to create, read, update, and delete tags on various Klaviyo objects such as campaigns, flows, lists and segments. See the API reference documentation for more info.
* [Data Privacy - Request Profile Deletion](ref:data-privacy): Use our new Data Privacy - Request Profile Deletion API endpoint to delete profiles with a provided identifier (i.e. `profile_id`, `email`, `phone_number`). See the API reference documentation for more info.

> ❗️ Breaking changes
>
> * Changed url path for [Create Template Render](ref:create_template_render) from `https://a.klaviyo.com/api/templates/{id}/render/` to `https://a.klaviyo.com/api/template-render/`
> * Changed url path for [Create Template Clone](ref:create_template_clone) from `https://a.klaviyo.com/api/templates/{id}/clone/` to `https://a.klaviyo.com/api/template-clone/`

*Update 2023-02-14*
* The `price` field can now be optionally supplied in the payload for [Create Catalog Item](ref:create_catalog_item) and [Update Catalog Item](ref:update_catalog_item) endpoints. This field can be used to set the price on the catalog item.

*Update 2023-02-07*
* A `channels` object can now be optionally supplied in the payload for the [Subscribe Profiles](https://developers.klaviyo.com/en/v2023-01-24/reference/subscribe_profiles) endpoint. When `channels` is provided, only the specified channels and message types will be subscribed. If `channels` is not provided, we will subscribe all channels for which identifiers (i.e. `phone_number` or `email`) are provided.

* The `profile_id` field can now be optionally supplied in the payload for the [Subscribe Profiles](https://developers.klaviyo.com/en/v2023-01-24/reference/subscribe_profiles) endpoint. This will be the id of the profile to subscribe.

# Revision `2022-10-17`
* Welcome to our new API changelog! This log will be kept up-to-date on the latest changes, bug fixes, and breaking changes to Klaviyo's APIs. Please note that this changelog only includes changes to new APIs released after **10/19/2022**.
* For further information about revisions and breaking changes, please review the [API versioning & deprecation policy](doc:api_versioning_and_deprecation_policy).
* Kickstart your migration to Klaviyo's new APIs with the [API comparison chart](doc:apis_comparison_chart), a detailed overview of what's changed from the v1/v2 endpoints to the new endpoints.

*Update 2023-01-20*

* The `list_id` attribute for the [Unsubscribe Profiles](ref:unsubscribe_profiles) endpoint is now an optional attribute instead of a required.

*Update 2023-01-11*

* The [Create Profile](ref:create_profile) and [Update Profile](ref:update_profile) endpoints now accept a phone number as an identifier even if SMS is not set up in the associated Klaviyo account. A successful call requires one other profile identifier attribute (`email`, `external_id`, or `anonymous_id`), in addition to a phone number.

*Update 2022-12-19*

* The reference documentation and OpenAPI Spec (OAS) for the [Create Template Render](ref:create_template_render) and [Create Template Clone](ref:create_template_clone) endpoints have been updated to reflect the correct required fields. This update resolves a minor bug in our documentation where a required field needed to call the endpoints successfully was missing. No changes have been made to these endpoints.

*Update 2022-11-02*

> ❗️ Breaking change 
>
> * Removed the `updated` filter parameter from the [Get Profiles endpoint](ref:get_profiles). This filter parameter was not intended for GA release and is not officially supported.
> * This change takes effect immediately due to site reliability concerns. Please refer to the [breaking change policy](doc:api_versioning_and_deprecation_policy#what-is-a-breaking-change) for more information.