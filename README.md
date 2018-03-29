# dot-globals

It's convenient for local global variables.

### Usage

Install from npm

```npm i dot-globals```

Create .globals.js file.

Add it to .gitignore.

Set up your global variables, for example:

```javascript
const env = process.env.NODE_ENV;
const envProduction = (env === 'production');

module.exports = {
    webpackHost: 'localhost',
    webpackPort: '3001',
    serverUrl: envProduction ? 'http://localhost' : 'http://localhost:3000'
};
```

Require with path param (project root folder is default)

```javascript
const GLOBALS = require('dot-globals')();
```

And use them, for example:
```
devServer: {
        host: GLOBALS.webpackHost,
        port: GLOBALS.webpackPort,
        inline: true,
        hot: true,
        proxy: {
            '/' : {
                target: GLOBALS.serverUrl,
                secure: false
            }
        },
```
