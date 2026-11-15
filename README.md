# Shipping Lanes Releases

Public release builds of **Shipping Lanes**. The game source is private. This repo only holds release builds so the Shipping Lanes launcher can find and download the latest patch without a token.

## How the launcher gets the latest patch

1. GET `https://api.github.com/repos/andymarkviera/Shipping-Lanes-Releases/releases/latest` (no auth needed).
2. Read `tag_name` as the version, for example `v2.9.0` or `v2.9.1`.
3. Pick the asset for the platform from `assets[]` and download its `browser_download_url`:
   - Windows: `Shipping-Lanes-Windows-x64.zip`
   - macOS: `Shipping-Lanes-macOS.zip`
4. Compare against the locally installed version. If the remote one is newer, download, unzip, and replace.

Launcher self-updates use the same release: `Shipping-Lanes-Launcher-Windows.exe` and `Shipping-Lanes-Launcher-macOS.zip`.

## Rules

- Tags are semver with a leading `v` (`v2.9.1`). Every release is a full build, never a diff.
- The release body holds the patch notes in Markdown.
- Never put tokens or secrets in the launcher. The public API is enough.
- The unauthenticated API rate limit is 60 requests an hour per IP, so check once at launch rather than polling.
