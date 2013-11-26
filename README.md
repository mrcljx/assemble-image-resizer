# assemble-image-resizer

[Assemble](http://assemble.io) plugin for resizing images found in your templates.

## Installation

From the same directory as your project's `Gruntfile` and `package.json`, install this plugin with the following command:

```bash
npm install assemble-image-resizer --save-dev
```

Modify your `assemble`-options in your `Gruntfile` so that the `assemble-image-resizer` plugin is used. You can also specify `imageResizer`-options (optional).

```js
grunt.initConfig({
  // ...
  
  assemble: {
    options: {
      // ...
      plugins: [require("assemble-image-resizer")],
      imageResizer: {
        srcRoot: "public", // default
        destRoot: "dest", // default
        subpath: "resize-cache", // default
        defaultFormat: "jpg", // default is "same as source"
      }
      // ...
    },
  },
  
  // ...
}
```
    
With the above configuration an image will

- be loaded from `public/image.png`,
- be stored in `dest/resize-cache/resized-image.jpg`, and
- have the URL `/resize-cache/resized-image.jpg`.

## Usage (with `assemble-liquid`)
   
```html 
<div>
  {{ "/images/selfie.png" | resize:"128x128#" | image_tag }}
</div>
```
    
With the example-configuration from above this will output

```html
<div>
  <img src="/resize-cache/selfie.png-128x128h.jpg">
</div>
```

## Possible resize formats

The syntax of the resize-argument is `[width]x[height][flags][.extension]`.

<dl>
  <dt><code>200x300</code></dt>
  <dd><strong>fit</strong> Resize image fit within 200x300 (touch from inside).</dd>

  <dt><code>200x</code></dt>  
  <dd>Resize image to width of at least 200.</dd>

  <dt><code>x300</code></dt>
  <dd>Resize image to height of at least 300.</dd>
  
  <dt><code>200x300#</code></dt>
  <dd><strong>fill</strong> Resize image to fill 200x300 (touch from outside).</dd>
  
  <dt><code>200x.jpg</code></dt>
  <dd>Resize image to width of at least 200 and convert it to a JPEG.</dd>
</dl>

## To-Do

- Add option to specify output format (`png` for alpha-support).
- Add option to modify JPEG-quality.
- Add an option that allows customization of missing-file handling (ignore, fail, or generate placeholder).
- Add `!`-flag to allow non-proportional resizing.
- Add support for conditional `<` and `>`-flags, that only resize *if smaller* and *if larger* respectively.

## Authors

**Marcel Jackwerth**

+ [http://twitter.com/sirlantis](http://twitter.com/sirlantis)
+ [http://github.com/sirlantis](http://github.com/sirlantis)

## Copyright and license

Copyright 2013 Marcel Jackwerth

[MIT License](LICENSE-MIT)
