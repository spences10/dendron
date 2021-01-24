---
id: 9ea46398-8cde-4c71-bbf8-790570a5182e
title: '2020-04-24'
desc: ''
updated: 1611474888837
created: 1611474757774
---

- Size image on the fly, like cloudinary: https://images.weserv.nl/
- Learning about writing scripts to the [[dom]] wit some neat ways to
  do things.

When trying to escape `<script>` tags it's better to generate it with
code.

```html
<script>
  var script = document.createElement('script')
  script.src = '/path/to/script.js'
  document.write(script.outerHTML)
</script>
```

- source:
  https://stackoverflow.com/questions/236073/why-split-the-script-tag-when-writing-it-with-document-write

You can also add parameters where you may have a custom attribute,
like with [[Fathom Analytics]]

```html
<script
  src="https://cdn.usefathom.com/3.js"
  site="YOUR-SITE-ID"
></script>
```

To generate the `site` attribute use something like this:

```js
const fathomScript = document.createElement('script')
fathomScript.src = 'https://cdn.usefathom.com/3.js'
fathomScript.setAttribute('site', 'YOUR-SITE-ID')
document.write(fathomScript.outerHTML)
```

- source:
  https://stackoverflow.com/questions/5292372/how-to-pass-parameters-to-a-script-tag
