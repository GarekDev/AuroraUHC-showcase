# Testing evidence

## Automated checks

The repository includes:

- `tests/run.php` for API 5 compatibility contracts, scenario construction,
  item/enchantment conversion, packet encoding and source-level regressions.
- `tools/smoke-server.ps1` for plugin packaging, server startup, world loading
  and fatal-startup detection.
- `tools/build-server.ps1` for rebuilding plugin archives and the resource
  pack from source.

The final local validation target is:

```text
Unit/static smoke checks passed
SMOKE PASS: test-world
```

## Manual verification

The live flow was verified on Falix using a Bedrock client:

- client connection through the Falix address;
- forced resource-pack acceptance;
- lobby and waiting-kit interaction;
- UHC configuration and start;
- player scatter and match progression;
- completion of a full UHC match.

## Known limitations

- Old Bedrock worlds may report unsupported legacy blocks, items or entity
  data during conversion.
- An arena is modified during a match and must be restored from a clean copy.
- RakNet is deprecated upstream; the currently verified Falix deployment is
  intentionally pinned to the working RakNet/core combination.
- Automated tests do not replace a real Bedrock client test.
