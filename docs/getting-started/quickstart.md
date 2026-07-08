# Quickstart

Use this quickstart to run the documentation site locally and validate content before publishing.

## Install dependencies

From the repository root, install the MkDocs dependencies:

```powershell
python -m pip install -r requirements.txt
```

## Run the local site

```powershell
mkdocs serve
```

Open the local URL printed by MkDocs. The development server reloads automatically when Markdown or configuration files change.

## Build the static site

```powershell
mkdocs build --strict
```

Strict mode fails the build for broken navigation, missing pages, invalid links, and configuration issues. Use it before every pull request.

## Add a page

1. Create a Markdown file under the appropriate `docs/` section.
2. Add the page to `mkdocs.yml` under `nav`.
3. Use sentence-case headings.
4. Add validation or operational guidance when the page describes a task.
5. Run a strict build.

## Troubleshooting

| Symptom | Resolution |
| --- | --- |
| `mkdocs` is not recognized | Install dependencies with `python -m pip install -r requirements.txt` |
| Page does not appear in navigation | Add the file to `mkdocs.yml` under `nav` |
| Mermaid diagram does not render | Confirm the code fence uses `mermaid` as the language |
| Strict build fails on links | Update relative links or add the missing page |

!!! tip
    Keep local builds boring. If a contributor can run one command and get a clean site, documentation work stays pleasant instead of turning into archaeology.
