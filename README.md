# path-captures

Malicious and suspicious request paths observed across production infrastructure. Updated daily.

## What This Is

A collection of URL paths commonly used by automated scanners, exploit kits, and bots probing web services. These paths are passively collected from real traffic hitting live domains -- not synthetic or theoretical.

## Lists

### `all.txt`

Every unique suspicious path observed, sorted alphabetically. One path per line. Suitable for use as a blocklist or feed into other tooling.

### `categories/`

Paths split by type:

- **php-probes.txt** -- PHP file probes (`.php`, `.php7`, `.php525`, etc.)
- **php-related.txt** -- Related PHP formats (`.phtml`, `.phar`)
- **path-traversal.txt** -- Directory traversal attempts (`../`, `%2e%2e/`)
- **sql-injection.txt** -- SQL injection patterns in URL paths
- **shell-upload.txt** -- Web shell and command execution paths
- **env-config.txt** -- Environment and config file probes (`.env`, `.git`, `.htaccess`, `wp-config`)
- **backup-files.txt** -- Backup and dump file probes (`.bak`, `.sql`, `.dump`)
- **devops-exposure.txt** -- CI/CD and container config exposure (`Dockerfile`, `Jenkinsfile`, `.kube`)
- **unrecognized.txt** -- Paths not matching known categories but absent from legitimate sitemaps

### `paths.json`

Machine-readable JSON array with metadata:

```json
[
  {
    "path": "/wp-login.php",
    "category": "php-probes",
    "first_seen": "2026-02-27T03:00:00Z",
    "hit_count": 47
  }
]
```

## Update Frequency

Lists sync once daily at 03:00 UTC.

## Usage

```bash
curl -sL https://raw.githubusercontent.com/SevensRequiem/path-captures/main/all.txt
```

## License

See [LICENSE](LICENSE).
