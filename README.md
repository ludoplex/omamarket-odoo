# Omamarket Odoo Apps

Browse Odoo Apps (https://apps.odoo.com) from the Omarchy bar. This is the one-lane edition of [Omamarket](https://github.com/ludoplex/omamarket); the full plugin covers six marketplaces in one panel.

The panel shows two blocks. The first block, labeled **From Mighty House**, lists the plugin publisher's own products (marked *sponsored*). The second block is the store's own catalog in the store's native order (purchases). Nothing is installed from the panel; clicking a listing opens the store page in your browser.

## Install

```sh
omarchy plugin add https://github.com/ludoplex/omamarket-odoo.git --enable
```

Then click **Odoo** in the bar and press **Install helper**. The helper (`omamarket.com`, one Cosmopolitan APE binary for x86_64 and aarch64, shared with Omamarket) is downloaded from the tag-pinned release in `helper.lock`, its sha256 is verified before it is made executable, and it is stored outside the plugin folder at `$XDG_DATA_HOME/omamarket/omamarket.com` (default `~/.local/share/omamarket/`). If Omamarket is already installed, the helper is already there and nothing is downloaded.

## Remove

```sh
omarchy plugin remove io.github.ludoplex.omamarket-odoo
```

Remove `~/.local/share/omamarket` and `~/.cache/omamarket` as well if no other Omamarket plugin is installed.

## External dependencies

- `curl`, `sha256sum`, `bash`, `xdg-open` (all shipped with Omarchy). The helper uses the system `curl` for every network request.
- No sudo or pkexec is required. No binfmt registration. The helper is launched as `/bin/sh <path>/omamarket.com` because an APE file is a valid shell script by specification and Quickshell's `Process` execs directly.
- Network targets: https://apps.odoo.com and `github.com` for the helper download. Responses are cached under `~/.cache/omamarket/`.
- No telemetry. Store links carry `utm_source=omamarket` so the publisher can attribute visits on its own listings.

## Source

The helper's source, tests and build script live in the Omamarket repository under `helper/`. This repository holds only the QML plugin, the installer script and the pinned helper lock; it is generated from `omamarket-lanes/template` and re-generated on every Omamarket release.

## License

MIT. See `LICENSE`.
