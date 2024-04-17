# strapi-provider-email-msgraph

Microsoft Graph email provider plugin for Strapi 4.x.

## Prerequisites

An app registration for the tenant with Mail.Send permission is required. You'll need:

- Tenant ID
- Client App ID
- Client App Secret

## Installation

We will create our own provider without publishing it on npm you can follow these steps:

- Create a providers folder in your application.
- Create your provider (e.g. ./providers/strapi-provider-<plugin>-<provider>)
- Then update your package.json to link your strapi-provider-<plugin>-<provider> dependency to the local path of your new provider.

  ```json
  {
    ...
    "dependencies": {
      ...
      "strapi-provider-email-msgraph": "file:providers/strapi-provider-email-msgraph",
      ...
    }
  }
  ```
  
- Then run either `yarn` or `npm install` (depending on which package manager you're using).

## Configuration

To use this provider setup your config/plugins.js file:
We need to use `provider: "strapi-provider-email-msgraph"` since this is local provider, we can't use provide `msgraph` as it is not published officialy by Strapi

```javascript
module.exports = ({ env }) => ({
  email: {
    provider: "strapi-provider-email-msgraph",
    providerOptions: {
      clientId: env("GRAPH_MAIL_CLIENT_ID"),
      clientSecret: env("GRAPH_MAIL_CLIENT_SECRET"),
      tenantId: env("GRAPH_MAIL_TENANT_ID"),
    },
    settings: {
      defaultFrom: "hello@example.com",
    },
  },
});
```
