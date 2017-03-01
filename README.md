# CWP Agency theme

This theme is a [subtheme](https://docs.silverstripe.org/en/3/developer_guides/templates/themes) of the [`cwp-base` theme](https://gitlab.cwp.govt.nz/cwp/new-theme). It provides a more visually appealing example for starting a theme for a CWP website.

## Installation

Install this theme module with Composer:

```
composer require cwp/new-theme_advanced
```

You may need to add this repository to your `composer.json` as a VCS repository.

## Getting started

This theme is designed to augment the base functionality and framework provided by the [`cwp-base` theme](https://gitlab.cwp.govt.nz/cwp/new-theme). As such, all of the documentation for the base theme is relevant to this theme as well. We suggest you familiarise yourself with this documentation.

As a general rule, we have endeavoured to constrain changes for this theme to CSS and Javascript wherever possible, as opposed to modifying the templates. As a subtheme, all templates in this theme will be applied over the top (with priority) of the base theme, and will be available to the SilverStripe template manifest under the "new-theme" theme name. You will not see this theme in theme selectors, etc.

If you need to modify template markup from the SilverStripe framework, other modules or even the base theme, you can copy them into this subtheme and modify them here.

## Development

### Setup

For development you will need to install the required NPM packages. Ensure you have changed into this theme's directory first:

```
cd themes/new-theme_advanced
npm install
```

### Backend changes

This theme and the base-theme also come with the [`cwp/theme-module`](https://gitlab.cwp.govt.nz/cwp/cwp-theme-module) which helps us to cleanup some parts of the CMS, rename some settings fields and provide a little bit of extra functionality to help these themes to work.

If you need to extend or modify these changes at all, you can control the theme's extensions with YAML configuration, or create your own extensions in your `mysite` code.

### Compiling assets

You can run the following NPM scripts to compile Javascript and SASS assets:

```
npm run build   # Produces unminified (development) distributable files in dist/
npm run package # Produces minified (production) distributable files in dist/
```

Or to "watch" for changes in real time as you develop (faster):

```
npm run watch  # Compiles as "build", then watches for changes and recompiles as necessary
```

> **Please note:** This subtheme's compiled Javascript assets are only relevant to this theme, and should be applied on top of the base theme's assets. Ensure that you include them in the correct order.
>
> For CSS, this theme contains _a fully compiled_ set of styles for both themes. You should only include this theme's CSS (not the base theme).

For example:

```
# File: templates/Page.ss - in the <head>
<link rel="stylesheet" href="{$ThemeDir}_advanced/dist/css/main.css">

# File: templates/Page.ss - near the bottom of the <body>
<script src="{$ThemeDir}/dist/js/main.js"></script>
<script src="{$ThemeDir}_advanced/dist/js/main.js"></script>
```

### Linting

Every now and then (e.g. before you commit) you should run a quick linter check over your Javascript and SASS source code:

```
npm run lint
```

## Versioning

This library follows [Semver](http://semver.org). According to Semver, you will be able to upgrade to any minor or patch version of this library without any breaking changes to the public API. Semver also requires that we clearly define the public API for this library.

All methods, with `public` visibility, are part of the public API. All other methods are not part of the public API. Where possible, we'll try to keep `protected` methods backwards-compatible in minor/patch versions, but if you're overriding methods then please test your work before upgrading.