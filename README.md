# Emojitown

This repository is a [Hugo module](https://gohugo.io/hugo-modules/)
that can be added to a Hugo site to display custom emoji or groups of custom emoji.

Emojitown consists of three parts:

- the `emojitown.html` shortcode in `layouts/shortcodes`
- an `emoji.json` file in `data`
- an emoji directory in `static` with 2,500+ custom emoji

## Make It Go

To add the emojitown repo to your Hugo site, add the following [module configuration](https://gohugo.io/hugo-modules/configuration/) to your site's config file:

```
[module]
[[module.imports]]
  path = "github.com/ianmadd/emojitown"
[[module.imports.mounts]]
  source = "data"
  target = "data"
[[module.imports.mounts]]
  source = "layouts/shortcodes"
  target = "layouts/shortcodes"
[[module.imports.mounts]]
  source = "static"
  target = "static"
```

Then add the module with [`hugo mod get`](https://gohugo.io/commands/hugo_mod_get/#hugo-mod-get):

```
hugo mod get github.com/ianmadd/emojitown
```

Hugo will generate or update two files, `go.mod` and `go.sum`.

From there you can use the emojitown shortcode to add custom emoji to your
Hugo site.

## Give Me the Doges

The emojitown shortcode has two possible parameters, `emoji` and `emojiparty`.

- `emoji`

  Emojitown will display a single emoji image if it finds one that matches the `emoji` parameter. For example, `{{< emojitown emoji="excellent" >}}`.

- `emojiparty`

  Emojitown will display every emoji image that partially or completely matches the
`emojiparty` parameter. For example, `{{< emojitown emojiparty="dance" >}}`.

## What's it doing?

Emojitown looks through the `emoji.json` file for a matching emoji name or names and then returns the matching file or files and displays them.

## Style

You might want to add some css to your site, maybe like this:

```
img.emoji{
    display: inline-block;
    height: 1.25em;
    margin: 0;
}
```