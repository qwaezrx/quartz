## Introduction
Renderers are responsible for displaying the output of your APIs. Some of these renderers display [[JSON]] content, some [[XML]] and some are responsible for the HTML.

There are many third-party renderers available to use. Commonly used renderers are:
- JSON renderer (built-in)
- browsable API renderer (built-in)
- XML renderer (third-party)
- [[YAML]] renderer (third-party)
- [[JSONP]] renderer (third-party)

# Response types
You can set `Accept` header in the [[HTTP request]] to set the type of content you want from the [[API]].

[[XML and JSON response types]]

[[HTTP response types]]

## DRF
By default DRF uses two renderers:
- `rest_framework.renderers.JSONRenderer`
- `rest_framework.renderes.BrowseableAPIRenderer`

You can change this setting in `settings.py` file.

### `djangorestframework-xml`
- `rest_framework_xml.renderers.XMLRenderer`

## Additional resources

[Different types of renderers](https://www.coursera.org/learn/apis/supplement/57qRB/different-types-of-renderers)