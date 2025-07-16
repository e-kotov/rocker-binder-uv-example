## Run this repository in a web browser using Binder. Push the button \>\> [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/e-kotov/rocker-binder-uv-example/HEAD?urlpath=lab)

### Local building and tests

Build:

```bash
docker build --platform linux/amd64 -f Dockerfile -t rocker-binder-uv-example:latest .
```

Run:

```bash
docker run --rm -p 8888:8888 rocker-binder-uv-example:latest
```
