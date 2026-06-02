# Publishing

Composer package: `vectorizer/ai`

Packagist publishes from the public GitHub repository and SemVer tags.

Submit `https://github.com/clv/vectorizer-ai-php` to Packagist under the `vectorizer/ai` package name. Configure the GitHub hook or Packagist GitHub integration so new tags are imported automatically.

After that, push a SemVer tag such as `v1.0.0`. The workflow validates `composer.json` and creates a GitHub release; Packagist should ingest the tag as the package version.
