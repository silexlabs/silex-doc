# Extend and customize Silex website builder

## Instance level

Import Silex as an npm dependency in a nodejs project, and accès Silex server side API, just like it is done her: https://github.com/silexlabs/Silex/blob/v3/src/ts/server/index.ts

Access thr config object directly before Silex uses it
https://github.com/silexlabs/Silex/blob/v3/src/ts/server/config.ts


```
import { config } from './config'
import { start } from './start'

start({
  ...config,
  port: 80,
})
```

Configurable options

| Name | Description | Default |
| -- | -- | -- |
| port | Port to listen to | 6805 (date of french latest revolution |
| url | Url of the server | - |
| midlewares | Use this array to add static or dynamic routes, replace the default midlewares, e.g. publisher, io, ssl | Default static routes and middlewares for loading, saving, publishing and SSL |
| upgrade | A function called on every website which needs an upgrade | Depends on Silex version |
| plugins | Array of plugins, client side and server side | [] |

## Site level

When Silex opens a website, it looks for a file named `.silex.json` which may contain these options:

* Path where to publish the HTML, CSS and JS files
* Path where to save the JSON files used for editing the website
* Path where to store the files uploaded by the user
* Plugins / apps for this website (client side)

## Client side API

Client side Silex is based on [GrapesJS](https://grapesjs.com/) which is also open source software and needs a lot of the credits

In order to load a plugin on the client side and use the client side API, you need to add it to the `plugins ` option, either at site level or instance level.

