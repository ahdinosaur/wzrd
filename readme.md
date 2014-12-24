# wzrd

Super minimal browserify development server. Inspired by [beefy](http://npmjs.org/beefy) but with less magic

## installation

```
npm install wzrd -g
```

**note** that you must have a copy of `browserify` installed as well. It can be either local (preferred) or global.

```
npm install browserify --save
```

## usage

```
wzrd app.js
```

This will start a local development server (default of `localhost:9966`) that serves all files in the current folder with the exception of `app.js`, which will be browserified instead. `wzrd` will spawn the command `browserify app.js` and send the output bundle back to the client.

If no `index.html` is present in the directory you run `wzrd` in, one will be generated for you that has a `<script src='app.js`></script>` in it.

### mappings

You can also specify a mapping:

```
wzrd app.js:bundle.js
```

This means if a request to the server comes in for `bundle.js`, `wzrd` will run the command `browserify app.js` and serve that.

### multiple entries

```
wzrd app.js:bundle.js foo.js:bar.js baz.js
```

### https

```
wzrd app.js --https
```

this will start a local https server (by default `https://localhost:4443`) and generate a self signed SSL certificate. You will get a certificate error in your browser, but if you ignore the error the app should load.
