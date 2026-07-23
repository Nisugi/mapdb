# Changelog

## [0.4.0](https://github.com/Nisugi/mapdb/compare/v0.3.0...v0.4.0) (2026-07-23)


### Features

* detect no-op re-submissions; source the CLI from repo variables ([4fbf502](https://github.com/Nisugi/mapdb/commit/4fbf50290425a1cd397ab92ad5244f78e685a493))
* detect stale-baseline submissions (concurrent-edit reverts) ([2aa15a3](https://github.com/Nisugi/mapdb/commit/2aa15a3c88dc2da3481b20345e24b509a19feab0))
* render StringProc code for review in the normalize check comment ([6e082d0](https://github.com/Nisugi/mapdb/commit/6e082d05ebb7b902e693c5a47c9fbb9bdb372c6e))
* sticky PR comment, proc vocabulary heuristic, deletion awareness ([22ff67f](https://github.com/Nisugi/mapdb/commit/22ff67f81174037fc1e046771a711a4eba9fe092))
* submission workflow - normalize check, post-merge canonicalize, CODEOWNERS ([4d3b6e9](https://github.com/Nisugi/mapdb/commit/4d3b6e9b26e78df9c922690f0f69b784918403f3))


### Bug Fixes

* **ci:** bound normalize preview output for full-map submissions ([da75d2a](https://github.com/Nisugi/mapdb/commit/da75d2a8f1f07f5ad9d941960c461669ba04788f))
* **rooms:** update 2 rooms via cartographer ([8802b22](https://github.com/Nisugi/mapdb/commit/8802b228d45e4c92c593bfa65753505a60bfa995))
* **rooms:** update 2 rooms via cartographer ([c1c2600](https://github.com/Nisugi/mapdb/commit/c1c26005c08d22a5a4f55f2789ba51ee6f8e9f18))
* **rooms:** update 2 rooms via cartographer ([8055612](https://github.com/Nisugi/mapdb/commit/80556124aba74b4508d083d145f413268c7aba5c))
* **rooms:** update 5 rooms via cartographer ([4792af7](https://github.com/Nisugi/mapdb/commit/4792af757cbb322a9690a4bc5005463b9e89faee))


### Reverts

* **rooms:** restore rooms 285, 1448, 2428, 30850, 33709 to v0.3.0 data ([ffe94e7](https://github.com/Nisugi/mapdb/commit/ffe94e75103af95a00026b93c5264c5b1fba0ccc))

## [0.3.0](https://github.com/elanthia-online/mapdb/compare/v0.2.1...v0.3.0) (2026-02-04)


### Features

* sync to latest mapdb 20260204 ([#6](https://github.com/elanthia-online/mapdb/issues/6)) ([f6bd376](https://github.com/elanthia-online/mapdb/commit/f6bd37639f447ced7613f7f0b8a4f6d4b717fbd3))

## [0.2.1](https://github.com/elanthia-online/mapdb/compare/v0.2.0...v0.2.1) (2025-07-22)


### Bug Fixes

* remove cartographer dependency to use bunx for latest version ([63112f5](https://github.com/elanthia-online/mapdb/commit/63112f5ff30fb6122ab2b6be7993fcdf37449c71))

## [0.2.0](https://github.com/elanthia-online/mapdb/compare/v0.1.0...v0.2.0) (2025-07-22)


### Features

* add build system and development tooling ([fd8f50d](https://github.com/elanthia-online/mapdb/commit/fd8f50dc5496af5114802f8795533e97376da83a))
* add build system and development tooling ([4ed9265](https://github.com/elanthia-online/mapdb/commit/4ed92653d929229e5884820f733b221e46710a0b))
* add GitHub Actions PR validation workflow ([5a9f85a](https://github.com/elanthia-online/mapdb/commit/5a9f85a867b7d83044e7ef2e356fd0312b49a052))
* add GitHub Actions PR validation workflow ([31ea435](https://github.com/elanthia-online/mapdb/commit/31ea4356976cff07fb45cd0aa5b13cd2b63a95b7))
* add release-please configuration and sync versions ([10a0d88](https://github.com/elanthia-online/mapdb/commit/10a0d885e04390974d7a75fdf9a633cbbd4236e3))
* update PR validation to use cartographer validate --input ([01f2c2d](https://github.com/elanthia-online/mapdb/commit/01f2c2dbd39494a298b164dba6d9350de8830052))
