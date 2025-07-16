## Run this repository in a web browser using Binder. Push the button \>\> [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/e-kotov/rocker-binder-uv-example/HEAD?urlpath=lab)


### How this was set up

Install uv (or see [https://docs.astral.sh/uv/getting-started/installation/](https://docs.astral.sh/uv/getting-started/installation/) ):

On macOS or Linux:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

On Windows:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

When in the root of the project directory, run:

```bash
uv init
```

Now install Python and pin it

```bash
uv python install 3.13
uv python pin 3.13
```

Add the modules:

```bash
uv add ipykernel geopandas geodatasets duckdb pandas matplotlib
```

Finally, pin the environment:

```bash
uv lock
```

If you change the environment (install different python version, add or remove modules, etc.), you can run `uv lock` again to update the lockfile.

You are all set, now just create a Dockerfile. See the example in [Dockerfile](Dockerfile) in this repository. It may seem long, but in fact it is verty simple.

To test the environment locally, on macOS or Linux you can do:

```bash
source ./.venv/bin/activate
```

On Windows in PowerShell you can do:

```powershell
./.venv/Scripts/activate
```

And test which Python version you have and where it is installed, on macOS or Linux:

```
python --version
which python
```

On Windows in PowerShell that would be:

```cmd
python --version
where.exe python
```


### Local building and tests

Build:

```bash
docker build --platform linux/amd64 -f Dockerfile -t rocker-binder-uv-example:latest .
```

Run:

```bash
docker run --rm -p 8888:8888 rocker-binder-uv-example:latest
```
