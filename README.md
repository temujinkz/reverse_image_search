# Reverse Image Search Bot

Telegram bot that takes an image, sticker, video, or GIF and returns reverse‑search links across multiple engines. Async Python, Poetry‑managed, type‑checked.

## Engines

- Google Images
- Yandex
- SauceNAO
- IQDB
- TinEye
- Pixiv (with auth)
- Trace.moe (anime)
- Baidu

Send media to the bot in DM or in a group, and it replies with direct search links. Supports auto‑search and inline mode.

## Stack

| | |
|---|---|
| Language | Python 3.11+ |
| Bot framework | python‑telegram‑bot (asyncio) |
| HTTP | aiohttp |
| Media | Pillow, imageio (ffmpeg) |
| Deps | Poetry |

## Run

```bash
# 1. Clone
git clone https://github.com/temujinkz/reverse_image_search.git
cd reverse_image_search

# 2. Configure
cp config.example.json config.json
# Fill in: bot token, SauceNAO/Pixiv keys, downloads folder, file_url

# 3. Install
poetry install

# 4. Start
poetry run start-bots
```

The `downloads` folder must be reachable at the URL you set in `file_url` so engines can fetch the uploaded image for searching.

## Configuration

Edit `config.json`:

```json
{
  "telegram_token": "...",
  "saucenao_api_key": "...",
  "pixiv_refresh_token": "...",
  "downloads_path": "./downloads",
  "file_url": "https://your-host.example.com/downloads"
}
```

## Structure

```
reverse_image_search/
  app.py              bot bootstrap
  engines/            per-engine search adapters
  providers/          media providers (Telegram, etc.)
  utils.py
pixiv_auth.py         standalone Pixiv refresh-token helper
pyproject.toml        Poetry deps + scripts (start-bots)
```

## License

LGPL‑3.0. See `LICENSE`.
