<!--
SPDX-FileCopyrightText: 2021 Andre Staltz

SPDX-License-Identifier: CC0-1.0
-->

:warning: **This repo was moved to https://github.com/ssbc/ssb-suggest-lite.** This archival will remain in this GitHub org `ssb-ngi-pointer` to demonstrate the outcome of the work done by the SSB NGI Pointer team during 2020 and 2021. The SSB NGI Pointer team is no longer active because we completed our grant project.

# ssb-suggest-lite

> An SSB secret-stack plugin for fetching profiles of authors that match a name

This is a lighter and simpler variant of [ssb-suggest](https://github.com/ssbc/ssb-suggest) built with ssb-db2. The differences with ssb-suggest are:

- Supports only `ssb-db2`
- Can only answer queries about peers you follow and `defaultIds` (does not load the cache with "recent authors" nor "recent abouts")
- Does not contain the field `following` in the results

## Install

```
npm install ssb-suggest-lite
```

## Usage

- Requires **Node.js 6.5** or higher
- Requires `secret-stack@^6.2.0`
- Requires `ssb-db2` and the `aboutSelf` plugin
- Requires `ssb-friends@>=4.4.4`

```diff
 SecretStack({appKey: require('ssb-caps').shs})
   .use(require('ssb-master'))
+  .use(require('ssb-db2'))
+  .use(require('ssb-db2/about-self'))
+  .use(require('ssb-friends'))
   .use(require('ssb-conn'))
   .use(require('ssb-blobs'))
+  .use(require('ssb-suggest-lite'))
   .call(null, config)
```

## API

`ssb.suggest.profile` works the same as with `ssb-suggest`, the only difference is that the results don't contain the field `following` nor the field `matchedName`.

## License

LGPL-3.0
