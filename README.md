# OneDrive Client for Linux

- Upstream README: https://github.com/abraunegg/onedrive/blob/master/README.md

- Docker images: https://github.com/lijuno/onedrive/pkgs/container/onedrive

- Usage:
  - For the first run, one needs to run container interatively to set the Microsoft credentials. Assuming the UID and GID of the current user are both 1000:
  ```
  docker run --rm -it \
      -v ${HOME}/onedrive/conf:/onedrive/conf \
      -v ${HOME}/onedrive/data:/onedrive/data \
      -e ONEDRIVE_UID:1000 \
      -e ONEDRIVE_GID:1000 \
      ghcr.io/lijuno/onedrive:stretch-latest \
      bash
  ```
  - Dryrun the download:
  ```
  docker run --rm \
      -v ${HOME}/onedrive/conf:/onedrive/conf \
      -v ${HOME}/onedrive/data:/onedrive/data \
      -e ONEDRIVE_UID:1000 \
      -e ONEDRIVE_GID:1000 \
      ghcr.io/lijuno/onedrive:stretch-latest \
      "onedrive --synchronize --download-only --confdir /onedrive/conf --syncdir /onedrive/data --dry-run"
  ```
  - Remove `--dry-run` to download for real; remove `--download-only` for two-way sync.
