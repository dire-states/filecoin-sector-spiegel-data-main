# sector-spiegel data: mainnet

Daily snapshot of every Filecoin **mainnet** miner that still has live sectors, for the
[sector-spiegel](https://github.com/dire-states/filecoin-sector-spiegel) site, served at
`https://dire-states.github.io/filecoin-sector-spiegel-data-main/`.

GitHub holds only the latest snapshot, as a single commit that each publish replaces. The full
history (one commit per snapshot) is kept locally on the machine that runs the fetch.

## Files

- `dataset.json`: marks this repo as the `mainnet` dataset. The fetch script refuses to write data
  from another network into it.
- `miners.json`: the overview index, loaded first by the site.
- `history.json`: changes between consecutive snapshots, appended by each fetch before it
  overwrites the previous snapshot. Per miner: sectors extended (and days added), expired,
  terminated early and added. The site reads it for the extensions list.
- `miners/<id>.json`: one file per miner, loaded when the miner is selected.

The layout is the same as the calibnet dataset; see its README and `MinerIndex` / `MinerData` in
`app/src/lib/types.ts`.

## Updating

From the app repo (uses the local mainnet node; `LOTUS_API` overrides):

```sh
scripts/publish.sh mainnet
```
