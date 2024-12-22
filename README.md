# npm Documentation

[![Publish](https://github.com/npm/documentation/actions/workflows/publish.yml/badge.svg)](https://github.com/npm/documentation/actions/workflows/publish.yml)

This is the documentation for [https://docs.npmjs.com/](https://docs.npmjs.com/).

[This repository](https://github.com/npm/documentation) contains the content for our documentation site, and the GitHub Actions workflows that generate the site itself.

## Quick start

1. `npm install` to download gatsby, our theme, and the dependencies
2. `npm run develop`: starts the test server at `http://localhost:8000`.
3. Update the content - it's Mdx, which is like markdown - in the `content` directory.
4. Review your content at `http://localhost:8000`. (Gatsby watches the filesystem and will reload your content changes immediately.)
5. Once you're happy, commit it and open a pull request at https://github.com/npm/documentation.
6. A CI workflow run will publish your PR to a GitHub Preview Page.
7. Once the content is reviewed, merge the pull request. That will [deploy the site](https://github.com/npm/documentation/actions/workflows/publish.yml).

Do you want to know more? Check out our [contributing guide](CONTRIBUTING.md).

## License

The npm product documentation in the content, and static folders are licensed under a [CC-BY 4.0 license](LICENSE).

All other code in this repository is licensed under a [MIT license](LICENSE-CODE).

When using the GitHub logos, be sure to follow the [GitHub logo guidelines](https://github.com/logos).[build-system]
requires = ["hatchling", "hatch-vcs"]
build-backend = "hatchling.build"

[project]
name = "urlscan"
dynamic = ["version"]
description = "View/select the URLs in an email message or file"
readme = "README.md"
license = "GPL-2.0-or-later"
authors = [
    { name = "Scott Hansen", email = "tech@firecat53.net" },
]
keywords = [
    "email",
    "mutt",
    "tmux",
    "urlscan",
    "urlview",
]
classifiers = [
    "Development Status :: 5 - Production/Stable",
    "Environment :: Console",
    "Environment :: Console :: Curses",
    "License :: OSI Approved :: GNU General Public License v2 (GPLv2)",
    "Operating System :: OS Independent",
    "Programming Language :: Python",
    "Programming Language :: Python :: 3.7",
    "Programming Language :: Python :: 3.8",
    "Programming Language :: Python :: 3.9",
    "Programming Language :: Python :: 3.10",
    "Programming Language :: Python :: 3.11",
    "Programming Language :: Python :: 3.12",
    "Topic :: Utilities",
]
dependencies = [
    "urwid>=1.2.1",
]

[project.scripts]
urlscan = "urlscan.__main__:main"

[project.urls]
Homepage = "https://github.com/firecat53/urlscan"

[tool.hatch.version]
source = "vcs"
fallback-version = "0.0.0"

[tool.hatch.build.hooks.vcs]
version-file = "urlscan/_version.py"

[tool.hatch.build.targets.wheel.shared-data]
LICENSE = "share/doc/urlscan/LICENSE"
"README.md" = "share/doc/urlscan/README.md"
"urlscan.1" = "share/man/man1/urlscan.1"

[tool.hatch.build.targets.sdist]
include = [
    "/urlscan",
    "urlscan.1",
]
