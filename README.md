# HashCheck

A static, client-side page that checks text against an expected hash. It supports MD5, SHA-1, SHA-256, SHA-384 and SHA-512, and the hashing happens entirely in the browser.

## URL parameters

| Param  | Description |
|--------|-------------|
| `text` | Text to hash (URL-encoded, hashed as UTF-8) |
| `hash` | Expected hash in hex (case-insensitive; `0x`, spaces and colons are ignored) |
| `algo` | `md5`, `sha1`, `sha256`, `sha384`, `sha512` (also accepts `SHA-256` etc.). Optional: if omitted, it's detected from the hash length, defaulting to SHA-256 |
| `trim` | `1` to trim surrounding whitespace before hashing (optional) |

Example:

```
https://<user>.github.io/<repo>/?text=hello&hash=2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824&algo=sha256
```

## Deploy to GitHub Pages

1. Create a repository (for example `hashcheck`), or name it `<user>.github.io` to serve it from the root.
2. Commit `index.html` to the `main` branch.
3. In the repo, go to **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, select `main` / `(root)`, and click Save.
4. After about a minute the site is live at `https://<user>.github.io/<repo>/`.

## Notes

- SHA hashes use the Web Crypto API, which only works over HTTPS. GitHub Pages serves over HTTPS. MD5 is implemented in plain JavaScript.
- Anything in the query string is stored in browser history and server access logs. Don't put secrets in the URL.
