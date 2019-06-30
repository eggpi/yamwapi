# yamwapi

A simple and modern Python wrapper for the [MediaWiki API](https://www.mediawiki.org/wiki/API:Main_page).

(Yes, yet another.)

Use me to talk to Wikipedia.

## Features

This library particularly suited for large batch jobs that perform many queries
to Wikipedia. Features include:

* Simple (but relatively low-level) API
* Persistent connections by default
* Uses POST for requests, allowing large payloads

This library is used by [Citation Hunt](https://tools.wmflabs.org/citationhunt),
and, as such, is in active development and production use.

## Examples

Fetching the Wikitext of a page requires a single method:

```python
import yamwapi

api = yamwapi.MediaWikiAPI('https://en.wikipedia.org/w/api.php', 'yamwapi UA')
print api.get_page_contents(title = 'Wikipedia')
```

Other methods and options can be accessed via a lower level API:

```python
api.options.maxlag = 10
print api.parse({'text': '{{ cn }}', 'contentmodel': 'wikitext'})
```

## But why another library?

If you're considering this library, also be sure to have a look at
[mwapi](https://pypi.org/project/mwapi/), which is similar, but slightly lower
level.
