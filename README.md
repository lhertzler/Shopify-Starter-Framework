# Shopify-Starter-Framework
## Commands

- `npm run start`        -> Starts Gulp watcher on `scripts` and `styles` directories.
- `npm run build`        -> Gulp builds the .min files from `scripts` and `styles`, but doesn't watch.
- `npm run watch`        -> Runs theme deploy and theme watch on development config.
- `npm run deploy-dev`   -> `theme deploy --env=development`
- `npm run deploy-stage` -> `theme deploy --env=staging`

## Project Setup

To build:

1. Clone repo locally

2. Install Shopify tooling:
   **Using Homebrew**

    - `brew tap shopify/shopify`
   

3. Install [Themekit](https://shopify.github.io/themekit/)
    - `brew install themekit` or `brew install -g themekit`

4. Run `npm install` && `npm install gulp` or `(npm  install -g gulp)`
   **Make sure to use latest version of nvm, nvm use --lts**

5. Get password from private app.

  - Shopify admin => Apps => Private Apps => Manage Private Apps => Create New
    Private App
    - Enter App Name
    - Under permissions _Theme templates and theme assets_ set to **Read Write** access.
    - Save
    - Copy **Password for config api-password**

6. Set up config.yml

``` yaml
# password, theme_id, and store variables are required.
#
# For more information on this config file:
# https://shopify.github.io/themekit/commands/#configure

development:
  password: [your-api-password]
  theme_id: "[your-theme-id]"
  store: [your-store].myshopify.com
  ignores:
    -themekit.ignores
  ignore_files:
      - config/settings_data.json
  
staging: 
  password: [your-api-password]
  theme_id: "[your-theme-id]"
  store: [your-store].myshopify.com
  ignores:
    -themekit.ignores
  ignore_files:
      - config/settings_data.json
  
production: 
  password: [your-api-password]
  theme_id: "[your-theme-id]"
  store: [your-store].myshopify.com
  timeout: 100s
  readonly: true

```

7. Run `gulp build` to compile

8. Run `theme deploy`

9. For development run `gulp` to watch directories and compile changes.
   In another terminal run `theme watch` to automatically deploy changes to Shopify.
