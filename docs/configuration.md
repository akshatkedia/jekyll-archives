## Configuration

Archives configuration is done in the site's `_config.yml` file, under the `jekyll-archives` key.

### Default configuration

```yml
jekyll-archives:
  enabled: []
  layout: archive
  permalinks:
    year: '/:year/'
    month: '/:year/:month/'
    day: '/:year/:month/:day/'
    tag: '/tag/:name/'
    category: '/category/:name/'
```

### Configuration options

#### Required and recommended settings
- [Enabled archives (`enabled`)](#enabled-archives)
- [Type-specific layouts (`layouts`)](#type-specific-layouts)

#### Optional settings
- [Default layout (`layout`)](#default-layout)
- [Permalinks (`permalinks`)](#permalinks)

---

#### Enabled archives

| Key       | Value type      | Values |
|-----------|-----------------|--------|
| `enabled` | String or Array | `'all'` or an array of any combination of `year`, `month`, `day`, `categories`, `tags` |

##### Description

This option sets which types of archives will be created. Must be set to an array of enabled archive types, or the string 'all' (to enable all archives).

##### Sample values

```yml
enabled: all
enabled:
  - categories
enabled:
  - year
  - month
  - tags
```

---

#### Default layout

| Key      | Value type | Values |
|----------|------------|--------|
| `layout` | String     | The layout name of the default archive layout |

##### Description

Sets the default layout to use if no type-specific layout (see [Type-specific layouts](#type-specific-layouts) below) for an archive is specified.

##### Sample values

```yml
layout: archive                  # _layouts/archive.html
layout: custom-archive-layout    # _layouts/custom-archive-layout.html
```

---

#### Type-specific layouts

| Key       | Value type                | Values |
|-----------|---------------------------|--------|
| `layouts` | Map, String &rarr; String | A map of layout type (`year`, `month`, `day`, `category`, `tag`) to its archive name. |

##### Description

Maps archive types to the layout they will be rendered in. Not all types need to be specified; those without a specific layout will fall back to the default layout.

##### Sample values

```yml
layouts:
  year: year-archive
  month: month-archive
  day: day-archive
  category: category-archive
  tag: tag-archive-layout
```

---

#### Permalinks

| Key          | Value type                | Values |
|--------------|---------------------------|--------|
| `permalinks` | Map, String &rarr; String | A map of layout type (`year`, `month`, `day`, `category`, `tag`) to its permalink format. |

##### Description

Maps archive types to the permalink format used for archive pages. The permalink style is the same as regular Jekyll posts and pages, but with different variables.

These variables are:

* `:year` for year archives
* `:year` and `:month` for month archives
* `:year`, `:month`, and `:day` for day archives
* `:name` for category and tag archives

*Note:* trailing slashes are required to create the archive as an `index.html` file of a directory.

##### Sample values

```yml
permalinks:
  year: '/archives/year/:year/'
  month: '/archives/month/:year-:month/'
  tag: '/archives/tag/:name/'
```
