# Estly voice-service source

Source snapshot for Estly Studio LLC’s VoiceStudio-based personal-voice service.

## Download

The versioned release contains the complete archived upstream trees, Estly’s
voice-service code, build files, dependency source supplements and license notices.
Use the ZIP attached to the [v2026.10.18 release](https://github.com/anchhh/estly-voice-source/releases/tag/v2026.10.18).
Verify the ZIP with the accompanying SHA-256 file; file checksums are inside it.

## License and scope

Estly-authored voice-service files are **AGPL-3.0-only**. Read `LICENSE` and
`NOTICE.txt`. Upstream code and third-party components retain their own licenses.
This repository does not include Estly’s customer portal, customer data or secrets.

## Contents

- `estly-wrapper/`: gateway, startup, bootstrap, Dockerfile and existing checks.
- `voicestudio-source.tar.gz`: full tracked VoiceStudio source at commit
  `3915a62cb482bb43117aaebab57d22745bd1cc21`.
- `moss-runtime-source.tar.gz`: full tracked MOSS runtime source at commit
  `8b7bcc9341b3b4ef3a3a58ba1338a7d85ff133eb`.
- `model-source/`: selected pinned model implementations, configurations and cards.
- `dependency-source/`, `licenses/`: source supplements and original notices.
- `deployed-python-inventory.json`: main Python environment inventory.
- `dependency-source-provenance.json`, `SOURCE-VERSIONS.json`: provenance.
- `prepare-source-build.py`: prepares a separate build context without executing it.

## Build

Extract the release ZIP, then run from its directory:

```sh
python3 prepare-source-build.py /path/to/new-build-directory
```

The helper prints the two Docker build commands. They build the upstream source
first, then Estly’s wrapper. The original wrapper Dockerfile also supports its
pinned upstream image. The first service boot downloads the selected model/runtime
assets. Use a new empty data volume and two distinct random server secrets of at
least 32 characters (`ESTLY_VOICE_KEY`, `OMNIVOICE_API_KEY`), supplied outside the
source tree. Never use production data or credentials for a reproduction build.

**Known limits:** a full source-only container rebuild has not been completed.
Upstream build steps include floating dependencies. The Python inventory excludes
the separate MOSS environment and system packages. Native-library binary-to-source
mapping and transitive build-source completeness are still being checked.
This snapshot makes the reviewed source available; it does not certify full
license compliance or authorize use of any person’s voice.

## Contact

Source questions: [andrew@estlystudio.com](mailto:andrew@estlystudio.com).
