[![tests](https://github.com/Metadrop/ddev-lighthouse/actions/workflows/tests.yml/badge.svg)](https://github.com/Metadrop/ddev-lighthouse/actions/workflows/tests.yml) ![project is maintained](https://img.shields.io/maintenance/yes/2025.svg)
![GitHub Release](https://img.shields.io/github/v/release/Metadrop/ddev-lighthouse)

* [What is DDEV Lighthouse Add-on?](#what-is-ddev-lighthouse-add-on)
* [Getting started](#getting-started)
* [Configuration](#configuration)
* [Running Tests](#running-tests)
* [Interpreting Results](#interpreting-results)

## What is DDEV Lighthouse Add-on?

This is a [DDEV](https://ddev.readthedocs.io) addon for running performance tests using Lighthouse, an open-source automated tool for improving web page quality. It utilizes the `tests/functional/lighthouserc.js` configuration file for test setup and saves reports in the `reports/lighthouse` folder of your project.

This is optimized for [Aljibe projects](https://github.com/Metadrop/Aljibe/), but can be used in any DDEV project.

Lighthouse analyzes performance, accessibility, best practices, and more of your web pages, generating detailed reports to help you enhance your site's quality and performance.

## Getting Started

Install this addon:

For DDEV v1.23.5 or above run

```sh
ddev add-on get Metadrop/ddev-lighthouse
```

For earlier versions of DDEV run

```sh
ddev get Metadrop/ddev-lighthouse
```

Once installed, make sure to restart your ddev project:

```sh
ddev restart
```

### Configuration

This addon uses the `tests/functional/lighthouserc.js` configuration file to customize tests according to your needs. You can modify this file following Lighthouse configuration guidelines.

### Running Tests

To execute Lighthouse tests, simply access your ddev environment and run the following command:

```sh
ddev lighthouse
```

Lighthouse will generate detailed reports and save them in the `reports/lighthouse` folder of your project.

### Interpreting Results

Once Lighthouse reports are generated, you can review them to identify areas for improvement in performance, accessibility, and more of your website.

Happy optimization!

**Contributed and maintained by [@Metadrop](https://github.com/Metadrop)**
