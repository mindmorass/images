# Container Images

Monorepo for Docker images with automatic CI/CD builds.

## Structure

Each directory contains a Dockerfile and related configuration:

```
├── tinyproxy/      # Lightweight HTTP/HTTPS proxy
│   ├── Dockerfile
│   └── tinyproxy.conf
└── .github/
    └── workflows/
        └── build.yml
```

## How It Works

The GitHub Actions workflow automatically:
1. Detects which directories changed
2. Builds only the affected images
3. Pushes to GitHub Container Registry (ghcr.io)

## Images

| Image | Description | Platform |
|-------|-------------|----------|
| tinyproxy | Alpine-based HTTP/HTTPS proxy | linux/arm64 |

## Usage

Pull images from GHCR:

```bash
docker pull ghcr.io/<owner>/tinyproxy:latest
```

### Manual Build

Build locally for ARM:

```bash
docker buildx build --platform linux/arm64 -t tinyproxy:local ./tinyproxy
```

## Adding New Images

1. Create a new directory with a `Dockerfile`
2. Commit and push - the workflow auto-detects new images
3. Manual trigger: `workflow_dispatch` with image name or "all"
