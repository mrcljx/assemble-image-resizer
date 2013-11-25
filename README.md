# assemble-image-resizer

[Assemble](http://assemble.io) plugin for resizing images found in your templates.

## Installation

Modify your `assemble`-options in your `Gruntfile` so that the `assemble-image-resizer` plugin is used. You can also specify `imageResizer`-options (optional).

    grunt.initConfig({
      // ...
      
      assemble: {
        options: {
          // ...
          plugins: [require("assemble-image-resizer")],
          imageResizer: { // these are the defaults
            srcRoot: "public",
            destRoot: "dest",
            subpath: "resize-cache"
          }
          // ...
        },
      },
      
      // ...
    }
    
In the example above a resized image will be stored in `dest/resize-cache/resized-image-123.jpg` while the url will be `/resize-cache/resized-image-123.jpg`.

## Usage (with `assemble-liquid`)
    
    <div>
      {{ "/images/selfie.png" | resize:"128x128#" | image_tag }}
    </div>
    
With the example-configuration from above this will output

    <div>
      <img src="/resize-cache/selfie.png-128x128h.jpg">
    </div>

## Possible resize formats

<dl>
  <dt><code>200x300</code></dt>
  <dd><strong>fit</strong> Resize image fit within 200x300 (touch from outside).</dd>

  <dt><code>200x</code></dt>  
  <dd>Resize image to width of at least 200.</dd>

  <dt><code>x300</code></dt>
  <dd>Resize image to height of at least 300.</dd>
  
  <dt><code>200x300#</code></dt>
  <dd><strong>fill</strong> Resize image to fill 200x300 (touch from inside).</dd>
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
