# Github Action Tutorial

A minimal Python template repository for GitHub Actions demonstrations. This template includes tests (pytest) and autopep8.

Structure:

```text
app/
  └─ hello.py
tests/
  └─ test_hello.py
requirements.txt
.github/workflows/test.yml
```

This example intentionally does not include a packaging workflow; you'll add it as a hands-on exercise.

## Local packaging

You can quickly build a standalone executable for this small project with PyInstaller.

On macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate  # macOS/Linux
.venv/bin/pip install -r requirements.txt
.venv/bin/pyinstaller --onefile app/hello.py
ls -la dist
```

On Windows PowerShell:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\Activate.ps1
.venv\Scripts\pip.exe install -r requirements.txt
.venv\Scripts\pyinstaller.exe --onefile app/hello.py
dir dist
```

## Add packaging workflow (exercise)

You can try implement a simple sequential workflow that first builds macOS arm64 and then Windows x64 packages in `.github/workflows/package.yml`.

If you have finished composing or encountered some troubles, you may see `solutions/package.yml` — this builds the two packages in sequence and uploads two artifacts (`hello-macos-arm64` and `hello-windows-x64`).

There is also a enhanced version that uses a matrix to build multiple Python versions and OSes in parallel in `solutions/package-matrix.yml`. You may check it out after finishing the exercise.

Steps:

1. Copy `solutions/package.yml` into `.github/workflows/package.yml`.
2. Commit and push; this will trigger the workflow via `workflow_dispatch` if you run it manually, or on `push` tags.
3. Check the workflow run and download artifacts from the run summary.
