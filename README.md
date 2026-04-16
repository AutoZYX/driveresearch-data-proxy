# driveresearch-data-proxy

Thin GitHub Pages site bound to `data.driveresearch.tech`. It embeds the live Streamlit dashboard at `driveresearchdata.streamlit.app` in a full-viewport iframe, so users land on a branded DRIVEResearch URL while still viewing the live platform.

## Why this exists

Streamlit Community Cloud's free tier does not support custom domains. This repo is the smallest possible GH Pages site that:

1. Owns `data.driveresearch.tech` (via `CNAME` + Let's Encrypt on GH Pages).
2. Embeds the actual dashboard via iframe.
3. Falls back to a direct redirect if the iframe fails to load within 15 s.

## DNS setup (on Alibaba Cloud)

In the DNS console for `driveresearch.tech`, add:

```
Type     Host    Value                      TTL
CNAME    data    autozyx.github.io.         10 min
```

Then in this repo's GitHub **Settings → Pages**:
- Source: `main` branch, `/` folder
- Custom domain: `data.driveresearch.tech`
- Enforce HTTPS: ☑ (after cert is provisioned)

## When the upstream Streamlit URL changes

Edit the `src=` in `index.html` and commit. Everything else stays the same.

## Canonical links

- Main site: <https://driveresearch.tech/>
- Upstream dashboard: <https://driveresearchdata.streamlit.app/>
- Dashboard source: <https://github.com/AutoZYX/NDS-Label-Platform>
