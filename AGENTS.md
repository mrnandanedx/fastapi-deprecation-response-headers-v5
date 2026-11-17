# Working in this repo

- Stay inside this repo folder. Do not read or edit files outside it.
- Create a new branch off `master` for your work and commit everything when done.
- Run tests inside Docker, not on the host. From the repo root:

```
docker run --rm --platform linux/amd64 -v "$PWD":/app -w /app \
  vcode-env:fastapi-deprecation-response-headers \
  python -m pytest tests/<test_file>.py -q -p no:cacheprovider -W "ignore::DeprecationWarning"
```

The `-W` flag is needed: a newer `anyio` emits a DeprecationWarning that the repo's pytest config turns into a collection error.

- Do not edit, loosen or delete existing tests to make them pass.
