# Test repo to show different .RelPermalink behaviour in Hugo

Test to show that .RelPermalink resolves differently in `<a href..` and `<option...`

## Using

This repo requires the Ananke theme.

1. Clone the repo.

    ```
    git clone https://github.com/honzik20/relpermalinkTest.git
    ```

2. Get the Ananke submodule:

    ```
    git submodule update --init --recursive
    ```
## Verifying different behaviour

The site can be run offline to more easily test the behaviour.

1. Build the site with `hugo`
2. Open `public/index.html` in a browser
3. Follow the link: Got to topic
4. Click one of the versions.

The site uses a partial - `layouts/partials/version-switcher.html` - to generate two ways of choosing different versions of the page, a select menu and links. Both were built using the same range, both use {{ .RelPermalink }} to generate the URLs. But the URLs generated are different:

| Method                                                                                  | Result                |
|:----------------------------------------------------------------------------------------|:----------------------|
| `<a href="{{ .RelPermalink }}">{{ .Params.Version }}</a>`                               | `../versiontest.html` |
| `<option value="{{ .Site.BaseURL }}{{ .RelPermalink }}">{{ .Params.Version }}</option>` | `/versiontest.html`   |

The partial used to generate the version controls is `layouts/partials/version-switcher.html`