# node

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/chainguard-images/node/actions/workflows/release.yaml/badge.svg)](https://github.com/chainguard-images/node/actions/workflows/release.yaml)

WORK IN PROGRESS

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/node:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221128` | `sha256:9ba0f889918ea541c385fd45e025ca7bb7f88770b5e17ef3e1936d4a5cc36ae0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:9ba0f889918ea541c385fd45e025ca7bb7f88770b5e17ef3e1936d4a5cc36ae0) | `amd64` |
| `migration-20221121` | `sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f) | `amd64` |
| `migration-20221122` | `sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87) | `amd64` |
| `migration-20221126` | `sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5) | `amd64` |
| `migration-20221127` | `sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696) | `amd64` |
| `latest` | `sha256:19f655fa9814cc3f249b9b0d8865a31bfe0536d4d4a38ed30959a29561f063ea`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:19f655fa9814cc3f249b9b0d8865a31bfe0536d4d4a38ed30959a29561f063ea) | `amd64` |
| `migration-20221119` | `sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974) | `amd64` |
| `migration-20221120` | `sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09) | `amd64` |
| `migration-20221123` | `sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d) | `amd64` |
| `migration-20221124` | `sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4) | `amd64` |
| `migration-20221125` | `sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d) | `amd64` |


## Usage

Minimal container image for running NodeJS apps

The image specifies a default non-root `node` user (UID 65532), and a working directory at `/app`, owned by that `node` user, and accessible to all users.

It specifies `NODE_PORT=3000` by default.

### Example

Navigate to the `example/` directory:

```
cd example/
```

The Dockerfile is based on Docker's [Build your Node image](https://docs.docker.com/language/nodejs/build-images/) tutorial, but uses the Chainguard node base image instead.

Build the application on the node base image.

```
docker build \
  --tag node-docker \
  --platform=linux/amd64 \
  .
```

Then you can run the image:

```
docker run \
  --rm -it \
  -p 8000:8000 \
  --platform=linux/amd64 \
  node-docker
```

...and test to see that it works:

```
curl --request POST \
  --url http://localhost:8000/test \
  --header 'content-type: application/json' \
  --data '{"msg": "testing" }'
```


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/node:latest | jq
```

Output:
```
Verification for cgr.dev/chainguard/node:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/node"
      },
      "image": {
        "docker-manifest-digest": "sha256:19f655fa9814cc3f249b9b0d8865a31bfe0536d4d4a38ed30959a29561f063ea"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "10bf29734e151e47a9984a641099b41b5bdc5e95",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQCm9anmN8SCecvo4U6EhE4oiao5w1ltux8TZJSm8/EtFQIhAKb57fc9mK8fp++3FsX5xezq7rl2ro8j2PIB1KoV+mXZ",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjNGFhM2NkNTlmOTZiOGI2MTEwMWMzMjYxNGRiYjk5OTBkMWVkZWY0Yzc1MzZhNzFjYzk5MjY4M2I1ZGQ3MTA2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQzJxQ0R0cWlTQ3BzeGFuajhDVklrdzhlc1NPMW0yUWFNaEdDbHlTRXJORkFpQVpSUm4zTTVla2JPa2hoVXBFVEJ1dWxFS3BIN1Zwdi9sOXh6d1dVb1poRmc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUndha05EUVhsNVowRjNTVUpCWjBsVlJsWXpXbWhaY0VOeGNGaGpLMHhrUWl0SGNrMDBTemw0VW1aRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RWTlJFRjNUMFJSTkZkb1kwNU5ha2w0VFZSSk5VMUVRWGhQUkZFMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZSYnk5UVprMUJlVTlRTmpGVk5tdDZZM28zSzB0d1dFTlpVVWQ1UWpoVVFuUlhjbVlLZFV0WVJXWnZNV0ZwUTFSdVVtRnROMjEzUjNOemVESllORzlEU0VrMFJ6ZG1jM0oyZDI1a1RrVkhORFl5VW5oS1puRlBRMEZyYzNkblowcElUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMZVM5eENqUlVLekIyVGtKU1luZzNjR05MWVN0UEx5OW5kbE13ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUkZkMWx0V1hsUFZHTjZUa2RWZUU1VVJteE9SR1JvVDFSck5FNUhSVEpPUkVWM1QxUnNhVTVFUm1sT1YwcHJDbGw2Vm14UFZGVjNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XV3RIUTJselIwRlJVVUl4Ym10RFFrRkpSV1YzVWpWQlNHTkJaRkZFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlZFRjBkalpGUVVGQlJVRjNRa2ROUlZGRFNVUkJkMVp3T1RoUFdsVlhlREE1VG10bFdsUUthbE5uYVRVdlkyaGhUazVGY1RsQlVXd3dZVFpJZVRKbVFXbENXbTh3WTNsclIzQlNNazFQVDNSamNrTTVRMEUxTmtKWFRsSnZOSE4xWTB0MmFWbDBiQW96T0c1WVpIcEJTMEpuWjNGb2EycFBVRkZSUkVGM1RtOUJSRUpzUVdwRlFXbERZMXBQTkhoVE4zaHFlRTlwTjIxMGJHaEdlRGxYUkZObmFrbEljVlZZQ2sxWVRtbFJSVzVuUm05VGJ6STNNR3gyYm1zeVNrNTNRbFpYY25wVlRWSXlRV3BCTjFaSFoxazRhMUZ6V2k5dk1XSm9UelJKUzFwb2RrMTRNRU5HWm1JS1dHRkRRM1J4VGprM05FUllTMnd3TkZsUk5HOUlablpTTVRoTVdXWlBUMUZUTXpROUNpMHRMUzB0UlU1RUlFTkZVbFJKUmtsRFFWUkZMUzB0TFMwSyJ9fX19",
          "integratedTime": 1669680532,
          "logIndex": 8047625,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "10bf29734e151e47a9984a641099b41b5bdc5e95",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3569738208",
      "sha": "10bf29734e151e47a9984a641099b41b5bdc5e95"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

