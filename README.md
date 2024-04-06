[![tests](https://github.com/Metadrop/ddev-lighthouse/actions/workflows/tests.yml/badge.svg)](https://github.com/Metadrop/ddev-lighthouse/actions/workflows/tests.yml) ![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

## ddev-lighthouse

This is a ddev-addon for running performance tests using Lighthouse, an open-source automated tool for improving web page quality. It utilizes the `tests/functional/lighthouserc.js` configuration file for test setup and saves reports in the `reports/lighthouse` folder of your project.

Lighthouse analyzes performance, accessibility, best practices, and more of your web pages, generating detailed reports to help you enhance your site's quality and performance.

## Getting Started

Install this addon by running the following command:

ddev get Metadrop/ddev-lighthouse

Once installed, make sure to restart your ddev project:

ddev restart

### Configuration

This addon uses the `tests/functional/lighthouserc.js` configuration file to customize tests according to your needs. You can modify this file following Lighthouse configuration guidelines.

### Running Tests

To execute Lighthouse tests, simply access your ddev environment and run the following command:

ddev lighthouse

Lighthouse will generate detailed reports and save them in the `reports/lighthouse` folder of your project.

### Interpreting Results

Once Lighthouse reports are generated, you can review them to identify areas for improvement in performance, accessibility, and more of your website.

We hope this addon helps you enhance the quality and performance of your web project. If you have any questions or issues, feel free to reach out to us.

Happy optimization!
