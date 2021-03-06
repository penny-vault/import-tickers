# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Added
- sub-task to delete a ticker from the parquet db

### Changed
- default tiingo assets is now 9000
- remove assets with len(ticker) > 4 and name = "" and last digit of ticker is U or W

### Deprecated

### Removed

### Fixed
- bug in yfinance that tries to update bar when asset is delisted and progressbar is disabled

### Security

## [0.4.0] - 2022-06-22
### Added
- Blacklist file to force removal of specific assets
- De-duplicate assets that belong to a single FIGI but have multiple listings (i.e. both a closed-end and mutual fund)

### Changed
- 'Economic Indicator' asset type renamed to 'FRED'
- Cleaned up logging to try and stay under the 100Kb limit @ healthchecks.io
- Ignore tickers from Tiingo that look like preferred shares, warrants or units
- Ignore tickers in DB marked as synthetic assets

## [0.3.0] - 2022-05-28
### Added
- Skip assets that have mixed case tickers
- Flag assets as `new` and `updated` to ease statistics tracking
- Option to load additional assets from a specified TOML file
- Add kill switch if counts from 3rd party services don't match expectations or if too many assets would be removed at once

### Changed
- Improved debug logs

## [0.2.0] - 2022-05-22
### Added
- Improved error handling when Polygon.io fails; job exits which is
  preferable to writing garbage to the assets database

## [0.1.0] - 2022-05-20
### Added
- Download stocks and etf's from Polygon
- Download mutual funds from Tiingo
- Enrich assets with Industry/Sector from yFinance!
- Encrich assets with Composite FIGI from Openfigi mapping API
- Save changed assets to database and backblaze

[Unreleased]: https://github.com/penny-vault/import-tickers/compare/v0.4.0...HEAD
[0.4.0]: https://github.com/penny-vault/import-tickers/compare/v0.3.0...v0.4.0
[0.3.0]: https://github.com/penny-vault/import-tickers/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/penny-vault/import-tickers/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/penny-vault/import-tickers/releases/tag/v0.0.1
