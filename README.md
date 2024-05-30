# book-production

A GitHub Actions based utility to run book production software

## `book-production` Action

Provides manually triggerable GitHub Action to do the following for OBP books:

1. Run [archive-pdf-urls](https://github.com/thoth-pub/archive-pdf-urls): this sends all links found in the PDF edition to the Internet Archive Wayback Machine
2. Run [chapter-splitter](https://github.com/OpenBookPublishers/chapter-splitter): this creates individual chapter PDFs from full PDF edition
3. Run [epublius](https://github.com/OpenBookPublishers/epublius): this creates HTML edition from EPUB edition
4. Run [cit-ex-obp-loader](https://github.com/OpenBookPublishers/cit-ex#obp-loader): this extracts citation data and writes it to Thoth

For PDF-only books, only 1 and 2 are run.

Newly created chapter PDFs and HTML edition are uploaded to OBP AWS S3 bucket. In Thoth, chapter PDF/HTML Publications/Locations are created and given appropriate Landing Pages/Full Text URLs.

### Usage

On the [Action page](https://github.com/OpenBookPublishers/prod-assistant/actions/workflows/script-tasks.yml), select the "Run workflow" dropdown. Input the book's DOI in the appropriate field then click the green "Run workflow" button.

Only the last four digits of the DOI should be supplied (e.g. the input value `9999` will expand to `https://doi.org/10.11647/OBP.9999`).

### Requirements

1. Full finalised metadata in Thoth (_except_ chapter PDF/HTML Publications/Locations)
2. PDF edition in OBP AWS S3 bucket
3. EPUB edition in OBP AWS S3 bucket (unless book is PDF-only)

### Access credentials

Requires read/write access to both Thoth and OBP AWS S3 bucket. Appropriate credentials should be stored in repository so no manual input is needed.

