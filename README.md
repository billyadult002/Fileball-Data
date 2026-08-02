# Fireball Data

Public, generated JSON and M3U outputs for Fireball clients. The source configuration and synchronization code remain in the private `billyadult002/Fileball` repository.

## Subscriptions

- [Latest](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/latest.m3u)
- [Regular](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/regular.m3u)
- [AV](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/av.m3u)
- [Movies](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/movies.m3u)
- [TV](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/tv.m3u)
- [Anime](https://raw.githubusercontent.com/billyadult002/Fileball-Data/main/output/anime.m3u)

`data/catalog.json` is the lightweight catalog, while `data/details/` contains full media records with provenance, episodes, and validated playback streams. `reports/latest-sync.json` contains aggregate synchronization status and sanitized failures.

The data is refreshed by GitHub Actions every two hours, with a deeper daily synchronization. Generated files may reference third-party streams; availability is controlled by each upstream provider.

The planned canonical delivery domain is `v8.hengmao.org`. Cloudflare delivery is not part of Mission 1 and is not yet claimed live.
