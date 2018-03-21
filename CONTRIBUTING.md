# Contributing To Simple Icons

Simple Icons welcomes contributions and corrections. Before contributing, please make sure you have read the guidelines below. If you decide to contribute anything, please do the following:

1. Fork this repository
1. Create a new branch from the latest `develop` (read more [here](https://guides.github.com/introduction/flow/))
1. Start hacking on the new branch
1. Commit and push to the new branch
1. Make a pull request

## Table of contents

* [Requesting An Icon](#requesting-an-icon)
* [Adding or Updating An Icon](#adding-or-updating-an-icon)
* [Labeling Issues](#labeling-issues)
* [Building Locally](#building-locally)

## Requesting An Icon

We welcome icon requests. Before you submit a new issue please make sure the icon:

* Is of a _popular_ brand.
* Has not already been requested.

When submitting a request for a new or updated icon include helpful information such as:

* **Issue Title:** The brand name. For example:
  * New Icons: `Request: GitHub Icon`
  * Icon Updates: `Update: GitHub Color` or `Update: GitHub Icon`

* **Issue Body:** Links to official sources for the brand's icon and colors (e.g. media kits, brand guidelines, SVG files etc.)

## Adding or Updating An Icon

### 1. Identify Official Logos and Colors

Most of the icons and brand colors on SimpleIcons have been derived from official sources. Using official sources helps ensure that the icons and colors in SimpleIcons accurately match the brand they represent. Thankfully, this is usually a simple process as organizations often provide brand guides and high quality versions of their logo for download.

Official high quality brand logos and brand colors can usually be found in the following locations:

1. About pages, Press pages, Media Kits, and Brand Guidelines.
1. Website headers (you can use [svg-grabber](https://chrome.google.com/webstore/detail/svg-grabber-get-all-the-s/ndakggdliegnegeclmfgodmgemdokdmg) for Chrome)
1. Favicons
1. Wikimedia (which should provide a source)

Working with an SVG version of the logo is best. In the absence of an SVG version, other vector filetypes may work as well (e.g. EPS, AI, PDF). In the absence of vector logos, a vector can be created from a high quality rasterized image, however this is much more labor intensive.

For color, the brand's primary color should be used. The official color of a brand is usually found in their brand guidelines, media kits, or some of the other locations mentioned above. If no official color can be identified, use the brand's primary web color or the most prominent color in the logo itself (please indicate why you choose the particular color in your pull request). Simple Icons stores brand colors in the standard 6 character hexadecimal format.

### 2. Extract The Icon From The Logo

There are many different tools for editing SVG files, some options include:

| Name | Description | Platform | Price |
| :---- | :---- | :----: | :----: |
| [Inkscape](https://inkscape.org/en/)| Vector Graphics Editor | Windows, Mac, Linux | Free |
| [Adobe Illustrator](https://www.adobe.com/products/illustrator.html) | Vector Graphics Editor | Windows, Mac | $ - $$$ |
| [IcoMoon](https://icomoon.io/) | Icon Editing/Management Tool | Online | Free |

Using your preferred tool you should:

1. Isolate the icon from any text or extraneous items.
1. Change the icon's viewbox/canvas/page size to 24x24.
1. Scale the icon to fit the viewbox, while preserving the icon's original proportions. This means the icon should be touching at least two sides of the viewbox.
1. Center the icon horizontally and vertically.
1. Remove all colors. The icon should be monochromatic.
1. Export the icon as an SVG.

### 3. Optimize The Icon

All icons in Simple Icons have been optimized with the [SVGO tool](https://github.com/svg/svgo). This can be done in one of two ways:

* The [SVGO Command Line Tool](https://github.com/svg/svgo)
  * Install SVGO
    * With npm: `npm install -g svgo`
    * With Homebrew: `brew install svgo`
  * Run the following command `svgo -p 3 icon.svg icon.min.svg`
* The [SVGOMG Online Tool](https://jakearchibald.github.io/svgomg/)
  * Click "Open SVG" and select an SVG file.
  * Set the precision to 3, leave the remaining settings at the default values.
  * Click the download button.

### 4. Annotate The Icon

Each icon in Simple Icons has been annotated with a number of attributes and elements to increase accessibility. These include:

* An svg element with:
  * An aria label (Note the format).
    * `aria-labelledby="simpleicons-adobephotoshop-icon"`
  * An img role attribute.
    * `role="img"`
  * A 24x24 viewbox.
    * `viewBox="0 0 24 24"`
  * The svg namespace.
    * `xmlns="http://www.w3.org/2000/svg"`
* A title element with id attribute (Note the format).
  * `<title id="simpleicons-adobephotoshop-icon">Adobe Photoshop icon</title>`

Here is _part of_ the svg for the Adobe Photoshop icon as an example:

```svg
<svg aria-labelledby="simpleicons-adobephotoshop-icon" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title id="simpleicons-adobephotoshop-icon">Adobe Photoshop icon</title>...</svg>
```

### 5. Check The Icon

The final icon should:

* Be properly annotated [as discussed above](#4-annotate-the-icon).
* Be monochromatic.
  * Remove all fill colors so that icon defaults to black.
* Be scaled to fit the viewbox, while preserving the icon's original proportions.
  * This means the icon should be touching at least two sides of the viewbox.
* Be vertically and horizontally centered.
* Be minified to a single line with no formatting.
* Not contain extraneous attributes.
  * This includes: `width`, `height`, `fill`, `stroke`, `clip`, `font`, etc.

Here is the svg for the Adobe Photoshop icon as an example:

```svg
<svg aria-labelledby="simpleicons-adobephotoshop-icon" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><title id="simpleicons-adobephotoshop-icon">Adobe Photoshop icon</title><path d="M0 .3v23.4h24V.3H0zm1 1h22v21.4H1V1.3zm4.8 4.48c0-.067.14-.116.224-.116.644-.033 1.588-.05 2.578-.05 2.772 0 3.85 1.52 3.85 3.466 0 2.54-1.842 3.63-4.102 3.63-.38 0-.51-.017-.775-.017v3.842c0 .083-.033.116-.115.116H5.916c-.083 0-.115-.03-.115-.113V5.78zm1.775 5.312c.23.016.412.016.81.016 1.17 0 2.27-.412 2.27-1.996 0-1.27-.786-1.914-2.122-1.914-.396 0-.775.016-.957.033v3.864zm8.607-1.188c-.792 0-1.056.396-1.056.726 0 .363.18.61 1.237 1.155 1.568.76 2.062 1.485 2.062 2.557 0 1.6-1.22 2.46-2.87 2.46-.876 0-1.62-.183-2.05-.43-.065-.033-.08-.082-.08-.165V14.74c0-.1.048-.133.114-.084.624.413 1.352.594 2.012.594.792 0 1.122-.33 1.122-.776 0-.363-.23-.677-1.237-1.205-1.42-.68-2.014-1.37-2.014-2.527 0-1.287 1.006-2.36 2.755-2.36.86 0 1.464.132 1.794.28.082.05.1.132.1.198v1.37c0 .083-.05.133-.15.1-.444-.264-1.1-.43-1.743-.43z"/></svg>
```

### 6. Update The JSON Data For SimpleIcons.org

Icon metadata should be added to the `_data/simple-icons.json` file. Each icon in the array has three required values:

  * The `title` of the new SVG.
  * A `hex` color value that matches the brand's primary color. All uppercase and without the `#` pound symbol.)
  * The `source` URL of the logo being used. (Be specific!)

Here is the object for the Adobe Photoshop icon as an example:

```json
{
    "title": "Adobe Photoshop",
    "hex": "00C8FF",
    "source": "https://wwwimages2.adobe.com/etc/clientlibs/beagle/ace/source/font/aceui-fonts.svg"
},
```

## Labeling Issues

We use several labels to help organize and identify issues. You can find all labels [here](https://github.com/simple-icons/simple-icons/labels). Here's what they represent and how we use them:

| Label Name | Description |
| :---- | :---- |
| [icon](https://github.com/simple-icons/simple-icons/labels/icon) | Issues for adding or updating an icon. |
| [docs](https://github.com/simple-icons/simple-icons/labels/docs) | Issues for improving or updating documentation. |
| [good first issue](https://github.com/simple-icons/simple-icons/labels/good%20first%20issue) | Issues we believe are simple and a good first stab at contributing to the project. |
| [help wanted](https://github.com/simple-icons/simple-icons/labels/help%20wanted) | Issues we would like help from the community to resolve. |
| [awaiting reply](https://github.com/simple-icons/simple-icons/labels/awaiting%20reply) | Issues awaiting reply from an individual (issue author or 3rd party) before it may be addressed. |
| [icon outdated](https://github.com/simple-icons/simple-icons/labels/icon%20outdated) | Issues regarding icons that are outdated, this can be the SVG or color or both. |

## Building Locally

* Make sure you have [Ruby](https://www.ruby-lang.org/en/downloads/) installed.
* Make sure you have [Jekyll](https://jekyllrb.com/) installed (using `$ gem install jekyll bundler`).
* Build and run the website locally using `$ jekyll serve`.
* Connect to the website in your browser via the "Server address" provided by the output of this command, e.g. `http://localhost:4000/`
